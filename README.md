#!/usr/bin/env python3
"""Convert your own copy of the SAToplam Writing Book PDF into data/questions.json.

Usage:  pip install pdfplumber
        python tools/extract_book.py path/to/book.pdf data/questions.json

The book is two-column: passage on the left, number + stem + options on the right.
Question numbers restart in each topic, so ids look like "boundaries-12".
Only use content you have the right to publish.
"""
import json, re, sys
import pdfplumber

TOPICS = [("boundaries", "Boundaries", "Topic 1: Boundaries"),
          ("fss", "Form, Structure, and Sense", "Topic 2: Form, Structure"),
          ("transitions", "Transitions", "Topic 3: Transitions"),
          ("synthesis", "Rhetorical Synthesis", "Topic 4: Rhetorical Synthesis")]
SPLIT_X = 0.50      # fraction of page width where right column starts
GAP = 28            # horizontal gap (pt) that marks a blank in the passage

def lines(words, x0, x1):
    rows = {}
    for w in words:
        if x0 <= w["x0"] < x1:
            rows.setdefault(round(w["top"] / 3), []).append(w)
    out = []
    for k in sorted(rows):
        ws = sorted(rows[k], key=lambda w: w["x0"])
        s = ws[0]["text"]
        for a, b in zip(ws, ws[1:]):
            s += (" ______ " if b["x0"] - a["x1"] > GAP else " ") + b["text"]
        out.append((ws[0]["top"], s))
    return out

def parse(pdf_path):
    pages = []
    with pdfplumber.open(pdf_path) as pdf:
        for p in pdf.pages:
            pages.append((p.extract_text() or "", p.extract_words(), p.width, p.height))
    topic, items, answers = None, {}, {}
    for text, words, W, Hh in pages:
        for t in TOPICS:
            if t[2] in text and "Questions" in text[:200]:
                topic = t
        if re.search(r"Number\s+Answer", text):
            tid = topic[0] if topic else None
            for n, a in re.findall(r"(\d+)\s+([A-D])\b", text):
                answers[(tid, int(n))] = a
            continue
        if not topic or "Must Know Tips" in text:
            continue
        # horizontal rule lines of dots separate questions
        seps = sorted(w["top"] for w in words if set(w["text"]) == {"."} and len(w["text"]) > 20)
        edges = [0] + seps + [Hh]
        for top, bot in zip(edges, edges[1:]):
            blk = [w for w in words if top <= w["top"] < bot and not w["text"].startswith("@satashkent")]
            right = lines(blk, W * SPLIT_X, W)
            left = lines(blk, 0, W * SPLIT_X)
            num = next((int(m.group(1)) for _, l in right if (m := re.fullmatch(r"(\d{1,3})", l.strip()))), None)
            if num is None:
                # number sits on the passage line, glued to right column text
                m = next((re.match(r"(\d{1,3})\s", l) for _, l in right if re.match(r"\d{1,3}\s", l)), None)
                num = int(m.group(1)) if m else None
            if num is None:
                continue
            rt = [re.sub(r"^\d{1,3}\s+", "", l).strip() for _, l in right]
            rt = [l for l in rt if l and l != str(num)]
            opts, stem, cur = {}, [], None
            for l in rt:
                m = re.match(r"([A-D])\)\s*(.*)", l)
                if m:
                    cur = m.group(1); opts[cur] = m.group(2)
                elif cur:
                    opts[cur] += " " + l
                else:
                    stem.append(l)
            if len(opts) < 4:
                continue
            items[(topic[0], num)] = {
                "id": f"{topic[0]}-{num}", "topic": topic[0], "topicName": topic[1], "n": num,
                "passage": " ".join(l for _, l in left).strip(),
                "stem": " ".join(stem).strip(),
                "options": [opts.get(k, "") for k in "ABCD"],
            }
    out = []
    for key, q in items.items():
        q["answer"] = answers.get(key, "")
        q["explanation"] = ""   # fill in later, or leave empty to use the topic rule
        out.append(q)
    return out

if __name__ == "__main__":
    data = parse(sys.argv[1])
    json.dump(data, open(sys.argv[2], "w", encoding="utf-8"), ensure_ascii=False, indent=1)
    miss = sum(1 for q in data if not q["answer"])
    print(f"{len(data)} questions written, {miss} without an answer key match")
