
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify — Your SAT Journey</title>
<style>
:root {
    --bg:#080b14;
    --surface:#111625;
    --surface2:#192136;
    --text:#f4f5ff;
    --muted:#929bb4;
    --primary:#8175ff;
    --border:#273047;
    --soft:#252344;
}
body.light {
    --bg:#f5f6fc;
    --surface:#ffffff;
    --surface2:#edf0f8;
    --text:#171a2c;
    --muted:#707991;
    --primary:#6557e8;
    --border:#e1e4ef;
    --soft:#eeebff;
}
* {box-sizing:border-box;margin:0;padding:0}
body {
    background:var(--bg);
    color:var(--text);
    font-family:Inter,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
    transition:.3s;
    min-height:100vh;
}
button,input,select {font:inherit}
button {cursor:pointer}
.hidden {display:none!important}
.logo {
    font-size:25px;
    font-weight:900;
    letter-spacing:-1.5px;
    color:var(--text);
}
.logo span {color:var(--primary)}
header {
    padding:22px 7%;
    display:flex;
    justify-content:space-between;
    align-items:center;
    border-bottom:1px solid var(--border);
}
.header-actions {display:flex;gap:10px;align-items:center}
.icon-btn {
    background:var(--surface2);
    border:1px solid var(--border);
    color:var(--text);
    border-radius:10px;
    padding:10px 13px;
}
.container {max-width:1150px;margin:auto;padding:35px 22px}
#onboarding {
    max-width:570px;
    margin:65px auto;
    padding:40px;
    background:var(--surface);
    border:1px solid var(--border);
    border-radius:24px;
    box-shadow:0 25px 90px #00000020;
}
.progress {
    height:5px;
    background:var(--surface2);
    border-radius:20px;
    margin-bottom:25px;
    overflow:hidden;
}
#progressFill {
    height:100%;
    width:25%;
    background:linear-gradient(90deg,#665bff,#b28aff);
    transition:.4s;
}
.counter {
    color:var(--primary);
    font-size:10px;
    letter-spacing:2px;
    font-weight:900;
    margin-bottom:24px;
}
.step {display:none;animation:appear .4s ease}
.step.active {display:block}
@keyframes appear {
    from {opacity:0;transform:translateY(12px)}
    to {opacity:1;transform:translateY(0)}
}
.step-icon {
    width:55px;height:55px;
    display:grid;place-items:center;
    border-radius:16px;
    background:var(--soft);
    font-size:26px;
    margin-bottom:24px;
}
h1 {
    font-size:34px;
    letter-spacing:-1.7px;
    line-height:1.2;
    margin-bottom:15px;
}
h1 span {color:var(--primary)}
.description {
    color:var(--muted);
    font-size:13px;
    line-height:1.8;
    margin-bottom:30px;
}
.field-label {
    display:block;
    font-size:12px;
    font-weight:700;
    margin-bottom:10px;
}
.field {
    width:100%;
    padding:16px;
    border:1px solid var(--border);
    border-radius:11px;
    background:var(--surface2);
    color:var(--text);
    outline:none;
    margin-bottom:18px;
}
.field:focus {border-color:var(--primary)}
.primary-btn {
    width:100%;
    border:0;
    border-radius:11px;
    padding:16px;
    color:white;
    background:linear-gradient(110deg,#6558ee,#9280ff);
    font-size:13px;
    font-weight:800;
    transition:.2s;
}
.primary-btn:hover {
    transform:translateY(-2px);
    box-shadow:0 10px 30px #7565ff45;
}
.back-btn {
    display:block;
    margin:18px auto 0;
    background:none;
    border:0;
    color:var(--muted);
    font-size:12px;
}
.target-card,.study-card {
    padding:20px;
    background:var(--surface2);
    border:1px solid var(--border);
    border-radius:13px;
    margin-bottom:14px;
}
.target-heading {
    display:flex;
    justify-content:space-between;
    font-size:13px;
    font-weight:700;
    margin-bottom:18px;
}
.target-heading strong {
    font-size:20px;color:var(--primary);
}
input[type=range] {width:100%;accent-color:var(--primary)}
.range-labels {
    display:flex;
    justify-content:space-between;
    color:var(--muted);
    font-size:10px;
    margin-top:8px;
}
.total-target {
    display:flex;
    justify-content:space-between;
    padding:18px;
    background:var(--soft);
    border-radius:12px;
    margin:20px 0;
    font-size:12px;
}
.total-target strong {color:var(--primary);font-size:18px}
.study-card {
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
}
.study-card h3 {font-size:13px;margin-bottom:5px}
.study-card p {font-size:10px;color:var(--muted)}
.study-card select {
    padding:10px;
    border-radius:8px;
    background:var(--surface);
    color:var(--text);
    border:1px solid var(--border);
}
.experience-option {
    display:flex;
    align-items:center;
    gap:12px;
    padding:17px;
    border:1px solid var(--border);
    background:var(--surface2);
    border-radius:12px;
    margin-bottom:12px;
    cursor:pointer;
}
.experience-option:has(input:checked) {
    border-color:var(--primary);
    background:var(--soft);
}
.experience-option input {accent-color:var(--primary)}
.experience-option div {flex:1}
.experience-option strong {font-size:12px;display:block;margin-bottom:6px}
.experience-option small {font-size:10px;color:var(--muted);line-height:1.5}
.note {font-size:11px;color:var(--muted);line-height:1.7;margin:20px 0}
#dashboard {max-width:1150px;margin:auto;padding:40px 22px}
.welcome {
    padding:35px;
    border-radius:20px;
    background:linear-gradient(115deg,#29225e,#5749a8,#7565db);
    color:white;
    margin-bottom:28px;
}
.welcome small {opacity:.75;font-size:11px;letter-spacing:2px}
.welcome h1 {margin:15px 0;font-size:36px}
.welcome p {font-size:13px;opacity:.8}
.section-title {font-size:19px;margin:30px 0 17px}
.stats {
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:15px;
}
.stat {
    background:var(--surface);
    border:1px solid var(--border);
    border-radius:15px;
    padding:22px;
}
.stat small {color:var(--muted);font-size:11px}
.stat h2 {font-size:29px;margin:12px 0;color:var(--primary)}
.stat p {font-size:10px;color:var(--muted)}
.lesson-grid {
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:18px;
}
.lesson {
    background:var(--surface);
    border:1px solid var(--border);
    border-radius:16px;
    padding:25px;
    transition:.2s;
}
.lesson:hover {transform:translateY(-4px);border-color:var(--primary)}
.lesson-icon {font-size:27px;margin-bottom:17px}
.lesson h3 {font-size:16px;margin-bottom:9px}
.lesson p {font-size:12px;color:var(--muted);line-height:1.7}
.lesson button {
    background:var(--soft);
    color:var(--primary);
    border:0;
    padding:11px 17px;
    border-radius:8px;
    margin-top:20px;
    font-weight:700;
    font-size:11px;
}
.dashboard-footer {
    text-align:center;
    color:var(--muted);
    font-size:10px;
    padding:45px 0;
}
#toast {
    position:fixed;
    bottom:25px;
    left:50%;
    transform:translateX(-50%);
    background:var(--surface2);
    border:1px solid var(--border);
    padding:13px 20px;
    border-radius:10px;
    font-size:12px;
    display:none;
    z-index:20;
}
@media(max-width:650px) {
    #onboarding {margin:35px 12px;padding:25px 20px}
    h1 {font-size:27px}
    .stats {grid-template-columns:1fr 1fr}
    .lesson-grid {grid-template-columns:1fr}
    .welcome h1 {font-size:28px}
    header {padding:17px 5%}
}
</style>
</head>
<body>

<header>
    <div class="logo">Prepify<span>.</span></div>
    <div class="header-actions">
        <button class="icon-btn" onclick="changeFont(-1)">A−</button>
        <button class="icon-btn" onclick="changeFont(1)">A+</button>
        <button class="icon-btn" onclick="toggleTheme()" id="themeBtn">☀️</button>
    </div>
</header>

<div id="onboarding">
    <div class="progress"><div id="progressFill"></div></div>
    <div class="counter" id="counter">STEP 01 OF 04</div>

    <div class="step active" id="step1">
        <div class="step-icon">✦</div>
        <h1>Your future starts <span>here.</span></h1>
        <p class="description">Welcome to Prepify. A smarter, more personalized way to prepare for the SAT. Let's build your journey together.</p>
        <label class="field-label">Your email address</label>
        <input class="field" id="email" type="email" placeholder="example@email.com">
        <p class="note">Create your learning profile and start working towards your dream university.</p>
        <button class="primary-btn" onclick="next(1)">Get Started →</button>
    </div>

    <div class="step" id="step2">
        <div class="step-icon">🎯</div>
        <h1>What's your <span>dream score?</span></h1>
        <p class="description">Set your target for both SAT sections. Every great achievement starts with a clear goal.</p>
        <div class="target-card">
            <div class="target-heading"><span>📐 SAT Math</span><strong id="mathValue">750</strong></div>
            <input type="range" id="math" min="200" max="800" step="10" value="750" oninput="updateScores()">
            <div class="range-labels"><span>200</span><span>800</span></div>
        </div>
        <div class="target-card">
            <div class="target-heading"><span>📖 Reading & Writing</span><strong id="readingValue">750</strong></div>
            <input type="range" id="reading" min="200" max="800" step="10" value="750" oninput="updateScores()">
            <div class="range-labels"><span>200</span><span>800</span></div>
        </div>
        <div class="total-target"><span>Total target</span><strong id="total">1500 / 1600</strong></div>
        <button class="primary-btn" onclick="next(2)">Continue →</button>
        <button class="back-btn" onclick="back(2)">← Go Back</button>
    </div>

    <div class="step" id="step3">
        <div class="step-icon">📅</div>
        <h1>Design your <span>daily routine.</span></h1>
        <p class="description">Consistency beats intensity. Choose how many lessons you can realistically complete each day.</p>
        <div class="study-card">
            <div><h3>📐 Math</h3><p>Daily Math lessons</p></div>
            <select id="mathLessons">
                <option value="1">1 lesson</option>
                <option value="2" selected>2 lessons</option>
                <option value="3">3 lessons</option>
                <option value="4">4 lessons</option>
                <option value="5">5 lessons</option>
            </select>
        </div>
        <div class="study-card">
            <div><h3>📖 Reading & Writing</h3><p>Daily English lessons</p></div>
            <select id="readingLessons">
                <option value="1">1 lesson</option>
                <option value="2" selected>2 lessons</option>
                <option value="3">3 lessons</option>
                <option value="4">4 lessons</option>
                <option value="5">5 lessons</option>
            </select>
        </div>
        <p class="note">You can adjust your daily learning goals anytime.</p>
        <button class="primary-btn" onclick="next(3)">Continue →</button>
        <button class="back-btn" onclick="back(3)">← Go Back</button>
    </div>

    <div class="step" id="step4">
        <div class="step-icon">🚀</div>
        <h1>Tell us about your <span>experience.</span></h1>
        <p class="description">Where are you in your SAT preparation journey?</p>
        <label class="experience-option">
            <input type="radio" name="experience" value="Beginner" checked>
            <div><strong>I'm completely new</strong><small>I'm just starting to learn about the SAT.</small></div>
        </label>
        <label class="experience-option">
            <input type="radio" name="experience" value="Intermediate">
            <div><strong>I've studied a little</strong><small>I know the basics and have practiced before.</small></div>
        </label>
        <label class="experience-option">
            <input type="radio" name="experience" value="Experienced">
            <div><strong>I'm already experienced</strong><small>I've taken practice tests and prepared before.</small></div>
        </label>
        <button class="primary-btn" onclick="finish()">Create My Learning Plan →</button>
        <button class="back-btn" onclick="back(4)">← Go Back</button>
    </div>
</div>

<div id="dashboard" class="hidden">
    <div class="welcome">
        <small>YOUR PERSONAL SAT DASHBOARD</small>
        <h1>Welcome to Prepify! ✨</h1>
        <p>Your goals are set. Your journey begins today.</p>
    </div>

    <h2 class="section-title">Your target scores</h2>
    <div class="stats">
        <div class="stat"><small>Math Target</small><h2 id="dashMath">750</h2><p>OUT OF 800</p></div>
        <div class="stat"><small>Reading & Writing</small><h2 id="dashReading">750</h2><p>OUT OF 800</p></div>
        <div class="stat"><small>Total Target</small><h2 id="dashTotal">1500</h2><p>OUT OF 1600</p></div>
    </div>

    <h2 class="section-title">Your daily study plan</h2>
    <div class="stats">
        <div class="stat"><small>Math lessons / day</small><h2 id="dashML">2</h2><p>DAILY GOAL</p></div>
        <div class="stat"><small>English lessons / day</small><h2 id="dashRL">2</h2><p>DAILY GOAL</p></div>
        <div class="stat"><small>Your experience</small><h2 id="dashExperience" style="font-size:20px">Beginner</h2><p>LEARNING LEVEL</p></div>
    </div>

    <h2 class="section-title">Start learning</h2>
    <div class="lesson-grid">
        <div class="lesson">
            <div class="lesson-icon">📐</div>
            <h3>SAT Math</h3>
            <p>Master algebra, advanced math, problem solving and data analysis.</p>
            <button onclick="notify('Math lessons are coming soon!')">Explore Math →</button>
        </div>
        <div class="lesson">
            <div class="lesson-icon">📖</div>
            <h3>Reading & Writing</h3>
            <p>Improve grammar, vocabulary, comprehension and writing skills.</p>
            <button onclick="notify('Reading & Writing lessons are coming soon!')">Explore English →</button>
        </div>
        <div class="lesson">
            <div class="lesson-icon">📝</div>
            <h3>Practice Tests</h3>
            <p>Test your knowledge with SAT-style practice questions.</p>
            <button onclick="notify('Practice tests are coming soon!')">Start Practice →</button>
        </div>
        <div class="lesson">
            <div class="lesson-icon">📊</div>
            <h3>My Progress</h3>
            <p>Track your preparation and monitor your achievements.</p>
            <button onclick="notify('Progress tracking is coming soon!')">View Progress →</button>
        </div>
    </div>
    <div class="dashboard-footer">PREPIFY © 2026 · BUILT FOR YOUR FUTURE</div>
</div>

<div id="toast"></div>

<script>
let fontSize = Number(localStorage.getItem("prepify-font") || 1);

function changeFont(direction) {
    fontSize = Math.max(.85,Math.min(1.2,fontSize + direction*.05));
    document.body.style.zoom = fontSize;
    localStorage.setItem("prepify-font",fontSize);
}

document.body.style.zoom=fontSize;

function toggleTheme() {
    document.body.classList.toggle("light");
    localStorage.setItem("prepify-theme",document.body.classList.contains("light")?"light":"dark");
}
if(localStorage.getItem("prepify-theme")==="light") {
    document.body.classList.add("light");
}

function showStep(n) {
    document.querySelectorAll(".step").forEach(s=>s.classList.remove("active"));
    document.getElementById("step"+n).classList.add("active");
    document.getElementById("counter").textContent=`STEP 0${n} OF 04`;
    document.getElementById("progressFill").style.width=(n*25)+"%";
}

function next(n) {
    if(n===1) {
        const email=document.getElementById("email").value.trim();
        if(!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
            notify("Please enter a valid email address.");
            return;
        }
    }
    showStep(n+1);
}

function back(n) {showStep(n-1)}

function updateScores() {
    const m=Number(document.getElementById("math").value);
    const r=Number(document.getElementById("reading").value);
    document.getElementById("mathValue").textContent=m;
    document.getElementById("readingValue").textContent=r;
    document.getElementById("total").textContent=(m+r)+" / 1600";
}

function finish() {
    const profile={
        email:document.getElementById("email").value.trim(),
        math:Number(document.getElementById("math").value),
        reading:Number(document.getElementById("reading").value),
        mathLessons:Number(document.getElementById("mathLessons").value),
        readingLessons:Number(document.getElementById("readingLessons").value),
        experience:document.querySelector('input[name="experience"]:checked').value
    };

    localStorage.setItem("prepify-profile",JSON.stringify(profile));
    showDashboard(profile);
}

function showDashboard(p) {
    document.getElementById("onboarding").classList.add("hidden");
    document.getElementById("dashboard").classList.remove("hidden");

    document.getElementById("dashMath").textContent=p.math;
    document.getElementById("dashReading").textContent=p.reading;
    document.getElementById("dashTotal").textContent=p.math+p.reading;
    document.getElementById("dashML").textContent=p.mathLessons;
    document.getElementById("dashRL").textContent=p.readingLessons;
    document.getElementById("dashExperience").textContent=p.experience;
}

function notify(message) {
    const toast=document.getElementById("toast");
    toast.textContent=message;
    toast.style.display="block";
    clearTimeout(window.toastTimer);
    window.toastTimer=setTimeout(()=>toast.style.display="none",2500);
}

// RESTORE SAVED PROFILE
try {
    const saved=JSON.parse(localStorage.getItem("prepify-profile"));
    if(saved && saved.email) showDashboard(saved);
} catch(e) {
    localStorage.removeItem("prepify-profile");
}
</script>
</body>
</html>
