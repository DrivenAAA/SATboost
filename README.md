
<style>
#pandaWords {
  display: none;
  width: 100%;
  padding: 32px;
  color: var(--text-color, #222);
  box-sizing: border-box;
}
#pandaWords * { box-sizing: border-box; }
.panda-header {
  display:flex; justify-content:space-between;
  align-items:center; margin-bottom:28px;
}
.panda-header h1 {font-size:28px;margin:0 0 7px;}
.panda-header p {color:#888;margin:0;font-size:14px;}
.panda-count {text-align:right;font-size:21px;font-weight:700;}
.panda-count small {display:block;color:#888;font-size:12px;font-weight:400;}
.panda-toolbar {display:flex;gap:12px;margin-bottom:18px;}
.panda-toolbar input,.panda-toolbar select {
  padding:12px 14px;border:1px solid #ddd;border-radius:7px;
  background:transparent;color:inherit;font-size:14px;
}
.panda-toolbar input {flex:1;min-width:0;}
.panda-progress {height:5px;background:#e8e8e8;border-radius:8px;overflow:hidden;margin-bottom:28px;}
#pandaProgressBar {height:100%;width:0;background:#222;transition:width .25s;}
.panda-card {
  min-height:340px;border:1px solid #e5e5e5;border-radius:10px;
  padding:26px;display:flex;flex-direction:column;
  align-items:center;justify-content:center;text-align:center;
}
.panda-card-top {width:100%;display:flex;justify-content:space-between;color:#999;font-size:11px;letter-spacing:1px;}
.panda-card h2 {font-size:38px;margin:42px 0 16px;}
#pandaDefinition {font-size:17px;max-width:600px;line-height:1.6;}
#pandaSynonym {color:#888;font-size:14px;}
.panda-btn {
  padding:11px 20px;border:1px solid #ddd;border-radius:7px;
  background:transparent;color:inherit;cursor:pointer;font-size:14px;
}
.panda-btn:hover {background:#f3f3f3;color:#222;}
#pandaReveal {margin-top:18px;}
#pandaActions {display:none;gap:10px;margin-top:20px;}
#pandaKnow {background:#222;color:white;border-color:#222;}
.panda-navigation {display:flex;justify-content:center;align-items:center;gap:24px;margin-top:24px;}
#pandaPosition {font-size:13px;color:#888;}
.panda-empty {padding:50px;text-align:center;color:#888;}
@media(max-width:650px) {
  #pandaWords {padding:18px;}
  .panda-header {align-items:flex-start;gap:15px;}
  .panda-toolbar {flex-direction:column;}
  .panda-card {min-height:300px;padding:18px;}
  .panda-card h2 {font-size:30px;}
}
</style>

<section id="pandaWords">
  <div class="panda-header">
    <div>
      <h1>Panda Words</h1>
      <p>Build your SAT vocabulary one card at a time.</p>
    </div>
    <div class="panda-count">
      <span id="pandaProgress">0 / 10</span>
      <small>Words learned</small>
    </div>
  </div>

  <div class="panda-toolbar">
    <input id="pandaSearch" type="search" placeholder="Search vocabulary...">
    <select id="pandaFilter">
      <option value="all">All words</option>
      <option value="unknown">Not learned</option>
      <option value="known">Learned</option>
    </select>
  </div>

  <div class="panda-progress"><div id="pandaProgressBar"></div></div>

  <div class="panda-card">
    <div class="panda-card-top">
      <span id="pandaNumber">WORD 01</span>
      <span>SAT VOCABULARY</span>
    </div>
    <h2 id="pandaWord">Abundant</h2>
    <p id="pandaDefinition" hidden></p>
    <p id="pandaSynonym" hidden></p>
    <button class="panda-btn" id="pandaReveal">Reveal definition</button>
    <div id="pandaActions">
      <button class="panda-btn" id="pandaUnknown">Don't Know</button>
      <button class="panda-btn" id="pandaKnow">Know</button>
    </div>
  </div>

  <div class="panda-navigation">
    <button class="panda-btn" id="pandaPrevious">Previous</button>
    <span id="pandaPosition">1 / 10</span>
    <button class="panda-btn" id="pandaNext">Next</button>
  </div>
</section>

<script>
(() => {
  // Original sample vocabulary. Add more entries using the same format.
  const words = [
    {word:"Abundant", definition:"Existing in large quantities.", synonym:"Plentiful, ample"},
    {word:"Ambiguous", definition:"Having more than one possible meaning.", synonym:"Unclear, vague"},
    {word:"Benevolent", definition:"Kind and generous.", synonym:"Compassionate, charitable"},
    {word:"Candid", definition:"Honest and direct.", synonym:"Frank, sincere"},
    {word:"Diligent", definition:"Working carefully and consistently.", synonym:"Hardworking, attentive"},
    {word:"Eloquent", definition:"Able to express ideas clearly and effectively.", synonym:"Expressive, articulate"},
    {word:"Feasible", definition:"Possible and practical to do.", synonym:"Achievable, viable"},
    {word:"Impartial", definition:"Treating everyone fairly.", synonym:"Unbiased, neutral"},
    {word:"Obscure", definition:"Not clear or easy to understand.", synonym:"Unclear, hidden"},
    {word:"Resilient", definition:"Able to recover from difficulties.", synonym:"Strong, adaptable"}
  ];

  const $ = id => document.getElementById(id);
  const section = $("pandaWords");
  let index = 0;
  let filtered = [...words];
  let known = [];

  try {
    known = JSON.parse(localStorage.getItem("satboostPandaKnown") || "[]");
    if (!Array.isArray(known)) known = [];
  } catch(e) { known = []; }

  function save() {
    localStorage.setItem("satboostPandaKnown", JSON.stringify(known));
  }

  function updateProgress() {
    $("pandaProgress").textContent = `${known.length} / ${words.length}`;
    $("pandaProgressBar").style.width =
      `${words.length ? known.length / words.length * 100 : 0}%`;
  }

  function render() {
    if (!filtered.length) {
      $("pandaWord").textContent = "No words found";
      $("pandaNumber").textContent = "";
      $("pandaDefinition").hidden = true;
      $("pandaSynonym").hidden = true;
      $("pandaReveal").hidden = true;
      $("pandaActions").style.display = "none";
      $("pandaPosition").textContent = "0 / 0";
      updateProgress();
      return;
    }

    index = Math.max(0, Math.min(index, filtered.length - 1));
    const item = filtered[index];
    const originalIndex = words.indexOf(item);

    $("pandaWord").textContent = item.word;
    $("pandaNumber").textContent =
      "WORD " + String(originalIndex + 1).padStart(2, "0");
    $("pandaDefinition").textContent = item.definition;
    $("pandaSynonym").textContent = "Synonyms: " + item.synonym;

    $("pandaDefinition").hidden = true;
    $("pandaSynonym").hidden = true;
    $("pandaReveal").hidden = false;
    $("pandaActions").style.display = "none";
    $("pandaPosition").textContent = `${index + 1} / ${filtered.length}`;

    updateProgress();
  }

  function reveal() {
    if (!filtered.length) return;
    $("pandaDefinition").hidden = false;
    $("pandaSynonym").hidden = false;
    $("pandaReveal").hidden = true;
    $("pandaActions").style.display = "flex";
  }

  function mark(isKnown) {
    if (!filtered.length) return;
    const originalIndex = words.indexOf(filtered[index]);

    known = known.filter(i => i !== originalIndex);
    if (isKnown) known.push(originalIndex);

    save();
    if (index < filtered.length - 1) index++;
    else index = 0;
    render();
  }

  function applyFilters() {
    const query = $("pandaSearch").value.trim().toLowerCase();
    const filter = $("pandaFilter").value;

    filtered = words.filter((item, i) => {
      const matchesSearch =
        item.word.toLowerCase().includes(query) ||
        item.definition.toLowerCase().includes(query) ||
        item.synonym.toLowerCase().includes(query);

      const matchesFilter =
        filter === "all" ||
        (filter === "known" && known.includes(i)) ||
        (filter === "unknown" && !known.includes(i));

      return matchesSearch && matchesFilter;
    });

    index = 0;
    render();
  }

  $("pandaReveal").addEventListener("click", reveal);
  $("pandaKnow").addEventListener("click", () => mark(true));
  $("pandaUnknown").addEventListener("click", () => mark(false));
  $("pandaNext").addEventListener("click", () => {
    if (filtered.length) { index = (index + 1) % filtered.length; render(); }
  });
  $("pandaPrevious").addEventListener("click", () => {
    if (filtered.length) { index = (index - 1 + filtered.length) % filtered.length; render(); }
  });
  $("pandaSearch").addEventListener("input", applyFilters);
  $("pandaFilter").addEventListener("change", applyFilters);

  // Expose a function for your existing sidebar Vocabulary button.
  window.showPandaWords = function() {
    document.querySelectorAll("main > section").forEach(el => {
      el.style.display = "none";
    });
    section.style.display = "block";
    render();
  };

  render();
})();
</script>
