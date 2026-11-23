
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify — SAT Learning Platform</title>
<style>
:root{
  --bg:#f5f7fb;--panel:#fff;--text:#172033;--muted:#788398;
  --line:#e8edf4;--primary:#6256e8;--primary2:#8177ff;
  --soft:#f0efff;--green:#159b72;--red:#df5968;--shadow:0 8px 28px #202b4510;
}
body.dark{
  --bg:#111522;--panel:#1a2030;--text:#eef1fa;--muted:#9aa5bb;
  --line:#2b3448;--primary:#9288ff;--primary2:#aaa3ff;
  --soft:#292644;--shadow:0 8px 28px #0003;
}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Inter,Arial,sans-serif;transition:.2s}
button,input,select{font:inherit}
button{cursor:pointer}
.app{display:flex;min-height:100vh}
.sidebar{
 width:250px;background:var(--panel);border-right:1px solid var(--line);
 padding:24px 15px;display:flex;flex-direction:column;position:fixed;
 top:0;bottom:0;left:0;z-index:10;overflow-y:auto
}
.logo{display:flex;align-items:center;gap:10px;padding:0 12px 28px;font-size:23px;font-weight:800}
.logo-mark{width:35px;height:35px;border-radius:11px;background:linear-gradient(135deg,var(--primary),#a69dff);display:grid;place-items:center;color:white}
.nav-label{font-size:10px;color:var(--muted);font-weight:800;letter-spacing:1.5px;padding:14px 12px 8px}
.nav-btn{border:0;background:transparent;color:var(--muted);padding:12px;border-radius:10px;text-align:left;width:100%;display:flex;gap:12px;align-items:center;font-size:13px;font-weight:650;margin:2px 0}
.nav-btn:hover,.nav-btn.active{background:var(--soft);color:var(--primary)}
.nav-icon{width:18px;text-align:center;font-size:16px}
.sidebar-bottom{margin-top:auto;border-top:1px solid var(--line);padding-top:14px}
.profile-mini{display:flex;align-items:center;gap:10px;padding:12px}
.avatar{width:35px;height:35px;border-radius:50%;background:var(--soft);color:var(--primary);display:grid;place-items:center;font-weight:800}
.profile-mini small{display:block;color:var(--muted);margin-top:3px}
.main{margin-left:250px;width:calc(100% - 250px);padding:30px 38px 60px;max-width:1600px}
.topbar{display:flex;align-items:center;justify-content:space-between;margin-bottom:30px;gap:15px}
.eyebrow{color:var(--muted);font-size:12px;margin-bottom:7px}
h1{font-size:27px;margin:0;font-weight:800;letter-spacing:-.7px}
h2{font-size:18px;margin:0 0 15px}
h3{font-size:15px;margin:0 0 8px}
.top-actions{display:flex;gap:9px;align-items:center}
.icon-btn{border:1px solid var(--line);background:var(--panel);color:var(--text);border-radius:10px;padding:10px 12px}
.primary{background:var(--primary);color:white;border:0;border-radius:10px;padding:11px 17px;font-weight:700}
.primary:hover{filter:brightness(1.08)}
.secondary{background:var(--panel);color:var(--text);border:1px solid var(--line);border-radius:10px;padding:10px 15px;font-weight:650}
.card{background:var(--panel);border:1px solid var(--line);border-radius:15px;padding:20px;box-shadow:var(--shadow)}
.grid{display:grid;gap:16px}
.stats{grid-template-columns:repeat(4,minmax(0,1fr));margin-bottom:20px}
.stat-label{color:var(--muted);font-size:12px}
.stat-value{font-size:27px;font-weight:800;margin:9px 0 5px}
.stat-note{font-size:11px;color:var(--muted)}
.dashboard-grid{grid-template-columns:1.5fr 1fr}
.progress{height:8px;border-radius:20px;background:var(--line);overflow:hidden;margin:12px 0}
.progress span{display:block;height:100%;background:var(--primary);border-radius:20px}
.section-heading{display:flex;justify-content:space-between;align-items:center;margin:25px 0 14px}
.section-heading h2{margin:0}
.course-grid{grid-template-columns:repeat(2,minmax(0,1fr))}
.course{display:flex;gap:15px;align-items:center}
.course-icon{width:45px;height:45px;border-radius:13px;display:grid;place-items:center;background:var(--soft);font-size:20px}
.course p{color:var(--muted);font-size:12px;margin:5px 0 0}
.course .secondary{margin-left:auto;white-space:nowrap}
.topic-list{display:grid;gap:9px}
.topic-row{display:flex;justify-content:space-between;align-items:center;padding:13px;border:1px solid var(--line);border-radius:11px;gap:10px}
.topic-row small{display:block;color:var(--muted);margin-top:4px}
.tag{font-size:10px;background:var(--soft);color:var(--primary);padding:5px 8px;border-radius:20px;font-weight:750}
.page{display:none}.page.active{display:block}
.filters{display:flex;gap:10px;flex-wrap:wrap;margin:18px 0}
.filters select,.search{background:var(--panel);color:var(--text);border:1px solid var(--line);border-radius:9px;padding:10px 12px}
.search{min-width:210px;flex:1}
.question-layout{display:grid;grid-template-columns:minmax(0,1fr) 250px;gap:17px}
.question-card{min-height:400px}
.q-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:22px}
.q-meta{display:flex;gap:8px;align-items:center}
.question-text{font-size:17px;line-height:1.7;margin:18px 0 22px;white-space:pre-line}
.options{display:grid;gap:10px}
.option{display:flex;align-items:flex-start;gap:12px;padding:13px;border:1px solid var(--line);border-radius:10px;cursor:pointer;line-height:1.5}
.option:hover{border-color:var(--primary)}
.option.selected{border-color:var(--primary);background:var(--soft)}
.option.correct{border-color:var(--green);background:#159b7210}
.option.wrong{border-color:var(--red);background:#df596810}
.option-letter{width:25px;height:25px;border-radius:7px;background:var(--bg);display:grid;place-items:center;font-size:12px;font-weight:800;flex-shrink:0}
.feedback{display:none;margin-top:17px;padding:14px;border-radius:10px;line-height:1.6;font-size:13px}
.feedback.show{display:block}
.feedback.good{background:#159b7212;color:var(--green)}
.feedback.bad{background:#df596812;color:var(--red)}
.q-actions{display:flex;justify-content:space-between;gap:10px;margin-top:22px;flex-wrap:wrap}
.side-info{display:grid;gap:12px;align-content:start}
.side-info .card{padding:16px}
.muted{color:var(--muted);font-size:12px;line-height:1.6}
.question-nav{display:grid;grid-template-columns:repeat(5,1fr);gap:7px;margin-top:12px}
.qnum{border:1px solid var(--line);background:var(--panel);color:var(--text);border-radius:7px;padding:8px 0;font-size:11px}
.qnum.current{background:var(--soft);border-color:var(--primary);color:var(--primary)}
.qnum.done{background:#159b7215;border-color:#159b7255}
.empty{text-align:center;padding:45px 20px;color:var(--muted)}
.table{width:100%;border-collapse:collapse;font-size:13px}
.table th,.table td{text-align:left;padding:13px;border-bottom:1px solid var(--line)}
.table th{color:var(--muted);font-size:11px}
.welcome{background:linear-gradient(115deg,#5147ce,#8277f5);color:white;border:0;padding:27px;margin-bottom:20px}
.welcome p{opacity:.85;font-size:13px;line-height:1.6;max-width:540px}
.welcome .primary{background:white;color:#5147ce}
.modal-bg{position:fixed;inset:0;background:#080d1acc;display:none;place-items:center;z-index:30;padding:20px}
.modal-bg.show{display:grid}
.modal{background:var(--panel);padding:27px;border-radius:16px;width:min(460px,100%);box-shadow:var(--shadow)}
.modal input,.modal select{width:100%;padding:12px;border:1px solid var(--line);background:var(--bg);color:var(--text);border-radius:9px;margin:7px 0 15px}
.modal label{font-size:12px;color:var(--muted);font-weight:700}
.modal h2{margin-bottom:7px}
.mobile-menu{display:none}
.login-screen{min-height:100vh;display:grid;place-items:center;padding:20px}
.login-box{width:min(430px,100%);background:var(--panel);padding:35px;border:1px solid var(--line);border-radius:18px;box-shadow:var(--shadow)}
.login-box input{width:100%;padding:13px;border:1px solid var(--line);background:var(--bg);color:var(--text);border-radius:9px;margin:8px 0 15px}
.login-box label{font-size:12px;color:var(--muted);font-weight:700}
.login-box .primary{width:100%;padding:13px}
.small-note{font-size:11px;color:var(--muted);line-height:1.6;margin-top:15px}
@media(max-width:1000px){.stats{grid-template-columns:repeat(2,1fr)}.dashboard-grid{grid-template-columns:1fr}.question-layout{grid-template-columns:1fr}.side-info{grid-template-columns:repeat(2,1fr)}}
@media(max-width:700px){
 .sidebar{transform:translateX(-100%);transition:.2s}.sidebar.open{transform:translateX(0)}
 .main{margin-left:0;width:100%;padding:22px 16px 45px}
 .mobile-menu{display:inline-block}.topbar{align-items:flex-start}
 .stats{gap:10px}.stat-value{font-size:23px}.course-grid{grid-template-columns:1fr}
 .side-info{grid-template-columns:1fr}
}
</style>
</head>
<body>

<div id="loginScreen" class="login-screen">
 <div class="login-box">
  <div class="logo" style="padding:0 0 25px"><span class="logo-mark">P</span> Prepify</div>
  <div class="eyebrow">YOUR SAT JOURNEY STARTS HERE</div>
  <h1 style="font-size:25px">Welcome back!</h1>
  <p class="muted">Sign in to continue your SAT preparation.</p>
  <form id="loginForm">
   <label>Email address</label>
   <input id="emailInput" type="email" placeholder="you@example.com" required>
   <button class="primary" type="submit">Continue with email →</button>
  </form>
  <p class="small-note">This is a front-end prototype. Email sign-in is not verified and the account is stored only in this browser. Real account security and cross-device sync require a backend.</p>
 </div>
</div>

<div class="app" id="app" style="display:none">
 <aside class="sidebar" id="sidebar">
  <div class="logo"><span class="logo-mark">P</span> Prepify</div>
  <div class="nav-label">STUDY</div>
  <button class="nav-btn active" data-page="dashboard"><span class="nav-icon">▦</span> Dashboard</button>
  <button class="nav-btn" data-page="bank"><span class="nav-icon">▤</span> Question Bank</button>
  <button class="nav-btn" data-page="practice"><span class="nav-icon">◷</span> Practice Test</button>
  <button class="nav-btn" data-page="mistakes"><span class="nav-icon">↻</span> My Mistakes</button>
  <button class="nav-btn" data-page="data"><span class="nav-icon">▥</span> My Data</button>
  <button class="nav-btn" data-page="materials"><span class="nav-icon">▧</span> Study Materials</button>
  <div class="nav-label">READING & WRITING</div>
  <button class="nav-btn topic-link" data-topic="Boundaries"><span class="nav-icon">A</span> Boundaries</button>
  <button class="nav-btn topic-link" data-topic="Form, Structure & Sense"><span class="nav-icon">A</span> Form, Structure & Sense</button>
  <button class="nav-btn topic-link" data-topic="Transitions"><span class="nav-icon">A</span> Transitions</button>
  <button class="nav-btn topic-link" data-topic="Rhetorical Synthesis"><span class="nav-icon">A</span> Rhetorical Synthesis</button>
  <div class="sidebar-bottom">
   <button class="nav-btn" id="themeBtn"><span class="nav-icon">◐</span> Toggle theme</button>
   <button class="nav-btn" id="logoutBtn"><span class="nav-icon">⇥</span> Log out</button>
   <div class="profile-mini"><div class="avatar" id="avatar">P</div><div style="min-width:0"><b id="profileEmail" style="font-size:12px">Student</b><small>Prepify student</small></div></div>
  </div>
 </aside>

 <main class="main">
  <div class="topbar">
   <div style="display:flex;align-items:center;gap:12px">
    <button class="icon-btn mobile-menu" id="menuBtn">☰</button>
    <div><div class="eyebrow" id="dateLabel">YOUR STUDY SPACE</div><h1 id="pageTitle">Dashboard</h1></div>
   </div>
   <div class="top-actions">
    <button class="icon-btn" id="fontDown">A−</button>
    <button class="icon-btn" id="fontUp">A+</button>
    <button class="icon-btn" id="themeTop">◐</button>
   </div>
  </div>

  <section class="page active" id="page-dashboard">
   <div class="card welcome">
    <div class="eyebrow" style="color:#e2dfff">YOUR PERSONAL SAT WORKSPACE</div>
    <h2 style="font-size:25px;margin:8px 0">Make every practice count.</h2>
    <p>Build your skills, focus on your weak areas, and track your SAT preparation in one place.</p>
    <button class="primary" onclick="showPage('bank')">Start practicing →</button>
   </div>
   <div class="grid stats">
    <div class="card"><div class="stat-label">Questions answered</div><div class="stat-value" id="statAnswered">0</div><div class="stat-note">Across all topics</div></div>
    <div class="card"><div class="stat-label">Accuracy</div><div class="stat-value" id="statAccuracy">—</div><div class="stat-note">Based on answered questions</div></div>
    <div class="card"><div class="stat-label">Saved questions</div><div class="stat-value" id="statSaved">0</div><div class="stat-note">Your bookmarks</div></div>
    <div class="card"><div class="stat-label">Mistakes to review</div><div class="stat-value" id="statMistakes">0</div><div class="stat-note">Questions answered incorrectly</div></div>
   </div>
   <div class="grid dashboard-grid">
    <div class="card">
     <div class="section-heading" style="margin:0 0 14px"><h2>Daily study goals</h2><span class="tag">Your plan</span></div>
     <div style="display:flex;justify-content:space-between;font-size:13px"><b>Math</b><span class="muted" id="mathGoalText">0 / 10 lessons</span></div>
     <div class="progress"><span id="mathGoalBar" style="width:0%"></span></div>
     <div style="display:flex;justify-content:space-between;font-size:13px;margin-top:20px"><b>Reading & Writing</b><span class="muted" id="rwGoalText">0 / 10 lessons</span></div>
     <div class="progress"><span id="rwGoalBar" style="width:0%"></span></div>
     <p class="muted" style="margin-top:17px">Your daily targets can be changed in your study settings.</p>
     <button class="secondary" onclick="openSettings()">Edit study goals</button>
    </div>
    <div class="card">
     <h2>Continue learning</h2>
     <div class="topic-list">
      <div class="topic-row"><div><b>Writing Question Bank</b><small>4 skills · Original sample questions</small></div><button class="secondary" onclick="showPage('bank')">Open</button></div>
      <div class="topic-row"><div><b>Practice Test</b><small>Mixed question practice</small></div><button class="secondary" onclick="startPractice()">Start</button></div>
      <div class="topic-row"><div><b>My Mistakes</b><small>Review your incorrect answers</small></div><button class="secondary" onclick="showPage('mistakes')">Review</button></div>
     </div>
    </div>
   </div>
   <div class="section-heading"><h2>Reading & Writing skills</h2><button class="secondary" onclick="showPage('bank')">View all</button></div>
   <div class="grid course-grid" id="dashboardTopics"></div>
  </section>

  <section class="page" id="page-bank">
   <div class="card">
    <div class="section-heading" style="margin:0"><div><h2>Question Bank</h2><p class="muted">Practice by skill and focus on your weak areas.</p></div><span class="tag">READING & WRITING</span></div>
    <div class="filters">
     <input class="search" id="searchInput" placeholder="Search questions or skills...">
     <select id="topicFilter">
      <option value="All">All topics</option>
      <option>Boundaries</option>
      <option>Form, Structure & Sense</option>
      <option>Transitions</option>
      <option>Rhetorical Synthesis</option>
     </select>
     <select id="statusFilter"><option value="All">All questions</option><option value="Unanswered">Not answered</option><option value="Correct">Correct</option><option value="Wrong">Incorrect</option><option value="Saved">Bookmarked</option></select>
    </div>
    <div class="question-layout">
     <div class="card question-card" style="box-shadow:none" id="questionArea">
      <div class="empty">Choose a topic or question to begin.</div>
     </div>
     <div class="side-info">
      <div class="card"><h3>Question progress</h3><div class="stat-value" id="bankProgress">0/0</div><div class="progress"><span id="bankProgressBar"></span></div><p class="muted">Questions you have answered.</p></div>
      <div class="card"><h3>Question navigator</h3><div class="question-nav" id="questionNav"></div></div>
      <div class="card"><h3>Study tip</h3><p class="muted">Read the full question carefully. After checking your answer, review the explanation to understand the rule or strategy.</p></div>
     </div>
    </div>
   </div>
  </section>

  <section class="page" id="page-practice">
   <div class="card">
    <div class="section-heading" style="margin-top:0"><div><h2>Practice Test</h2><p class="muted">A short mixed practice session using Prepify sample questions.</p></div><span class="tag">PRACTICE MODE</span></div>
    <div id="practiceIntro">
     <div class="grid stats" style="grid-template-columns:repeat(3,1fr)">
      <div class="card"><div class="stat-label">Questions</div><div class="stat-value">5</div></div>
      <div class="card"><div class="stat-label">Topics</div><div class="stat-value">4</div></div>
      <div class="card"><div class="stat-label">Mode</div><div class="stat-value" style="font-size:20px">Timed</div></div>
     </div>
     <p class="muted">This is a short practice set, not an official SAT test or score prediction.</p>
     <button class="primary" onclick="startPractice()">Start practice test →</button>
    </div>
    <div id="practiceArea" style="display:none"></div>
   </div>
  </section>

  <section class="page" id="page-mistakes">
   <div class="card"><div class="section-heading" style="margin-top:0"><div><h2>My Mistakes</h2><p class="muted">Questions you answered incorrectly. Try them again.</p></div><span class="tag">REVIEW</span></div><div id="mistakeList"></div></div>
  </section>

  <section class="page" id="page-data">
   <div class="grid stats">
    <div class="card"><div class="stat-label">Total answered</div><div class="stat-value" id="dataAnswered">0</div></div>
    <div class="card"><div class="stat-label">Correct answers</div><div class="stat-value" id="dataCorrect">0</div></div>
    <div class="card"><div class="stat-label">Incorrect answers</div><div class="stat-value" id="dataWrong">0</div></div>
    <div class="card"><div class="stat-label">Accuracy</div><div class="stat-value" id="dataAccuracy">—</div></div>
   </div>
   <div class="card"><h2>Performance by topic</h2><div id="topicPerformance"></div></div>
  </section>

  <section class="page" id="page-materials">
   <div class="card"><h2>Study Materials</h2><p class="muted">Useful official SAT preparation resources.</p>
    <div class="topic-list">
     <div class="topic-row"><div><b>College Board — SAT Suite</b><small>Official information about the SAT.</small></div><a href="https://satsuite.collegeboard.org/" target="_blank" class="secondary" style="text-decoration:none">Open ↗</a></div>
     <div class="topic-row"><div><b>Bluebook</b><small>Official digital testing application.</small></div><a href="https://bluebook.collegeboard.org/" target="_blank" class="secondary" style="text-decoration:none">Open ↗</a></div>
     <div class="topic-row"><div><b>Khan Academy</b><small>Free SAT preparation lessons and practice.</small></div><a href="https://www.khanacademy.org/test-prep/sat" target="_blank" class="secondary" style="text-decoration:none">Open ↗</a></div>
     <div class="topic-row"><div><b>College Board Question Bank</b><small>Official practice questions.</small></div><a href="https://satsuitequestionbank.collegeboard.org/" target="_blank" class="secondary" style="text-decoration:none">Open ↗</a></div>
    </div>
   </div>
  </section>
 </main>
</div>

<div class="modal-bg" id="setupModal">
 <div class="modal">
  <div class="logo" style="padding:0 0 15px"><span class="logo-mark">P</span> Prepify</div>
  <h2>Set up your study plan</h2>
  <p class="muted">Choose your targets and daily goals. You can change them later.</p>
  <form id="setupForm">
   <label>Target Math score (200–800)</label>
   <input type="number" id="targetMath" min="200" max="800" value="700" required>
   <label>Target Reading & Writing score (200–800)</label>
   <input type="number" id="targetRW" min="200" max="800" value="700" required>
   <label>Daily Math lessons</label>
   <input type="number" id="dailyMath" min="1" max="50" value="10" required>
   <label>Daily Reading & Writing lessons</label>
   <input type="number" id="dailyRW" min="1" max="50" value="10" required>
   <button class="primary" type="submit" style="width:100%">Save my study plan</button>
  </form>
 </div>
</div>

<script>
const topics=[
 "Boundaries",
 "Form, Structure & Sense",
 "Transitions",
 "Rhetorical Synthesis"
];

// These are original Prepify sample questions, not copied from the uploaded book.
const questions=[
 {id:1,topic:"Boundaries",difficulty:"Medium",text:"The research team collected data from several coastal regions ____ the results revealed a clear pattern in water temperature.",options:["A) regions, and the","B) regions; the","C) regions the","D) regions, the"],answer:1,explanation:"The sentence contains two independent clauses. A semicolon can correctly join two closely related independent clauses."},
 {id:2,topic:"Boundaries",difficulty:"Medium",text:"Although the experiment was initially considered unsuccessful ____ the researchers later discovered an important result.",options:["A) unsuccessful,","B) unsuccessful;","C) unsuccessful","D) unsuccessful:"],answer:0,explanation:"An introductory dependent clause beginning with “Although” is followed by a comma before the main clause."},
 {id:3,topic:"Form, Structure & Sense",difficulty:"Medium",text:"The collection of rare plants ____ carefully maintained by the university's biology department.",options:["A) are","B) were","C) is","D) have been"],answer:2,explanation:"The subject is “collection,” which is singular. The verb must therefore be singular: “is.”"},
 {id:4,topic:"Form, Structure & Sense",difficulty:"Hard",text:"By the time the final report was published, the scientists ____ the data for nearly three years.",options:["A) analyze","B) had been analyzing","C) will analyze","D) are analyzing"],answer:1,explanation:"The past perfect progressive describes an activity that continued over a period of time before another past event."},
 {id:5,topic:"Transitions",difficulty:"Medium",text:"The first design was inexpensive to produce. ____, it required frequent repairs, making it costly over time.",options:["A) For example","B) Nevertheless","C) Similarly","D) In addition"],answer:1,explanation:"“Nevertheless” signals a contrast between the low initial cost and the later repair expenses."},
 {id:6,topic:"Transitions",difficulty:"Hard",text:"Several studies have examined the effects of urban green spaces on air quality. ____, recent research has also explored their influence on residents' mental well-being.",options:["A) In contrast","B) As a result","C) Furthermore","D) Instead"],answer:2,explanation:"“Furthermore” adds another related point to the information already presented."},
 {id:7,topic:"Rhetorical Synthesis",difficulty:"Medium",text:"A student is writing about a museum exhibition. The student wants to emphasize that the exhibition includes works from different historical periods.\n\nNotes:\n• The exhibition opened in 2024.\n• It contains 60 paintings.\n• The paintings were created between 1600 and 1950.\n• The exhibition is located in the city art museum.\n\nWhich choice most effectively uses the notes to achieve the student's goal?",options:["A) The city art museum opened an exhibition in 2024.","B) The exhibition features 60 paintings created across a period spanning from 1600 to 1950.","C) The museum is located in the city center.","D) Sixty paintings are included in the exhibition."],answer:1,explanation:"Choice B directly emphasizes the range of historical periods represented by the paintings."},
 {id:8,topic:"Rhetorical Synthesis",difficulty:"Hard",text:"A student is writing about a scientific discovery. The student wants to compare the two methods used in the study.\n\nNotes:\n• Method A took 12 hours to complete.\n• Method B took 4 hours to complete.\n• Both methods produced results with similar accuracy.\n\nWhich choice best achieves the student's goal?",options:["A) The study used two methods to collect scientific data.","B) Method A and Method B both produced accurate results.","C) Although Method A took longer, both methods achieved similar levels of accuracy.","D) Method B was used in a scientific study."],answer:2,explanation:"Choice C compares the time required by each method while also highlighting their similar accuracy."}
];

let user=localStorage.getItem("prepify_email")||"";
let profile=JSON.parse(localStorage.getItem("prepify_profile")||"null");
let answers=JSON.parse(localStorage.getItem("prepify_answers")||"{}");
let saved=JSON.parse(localStorage.getItem("prepify_saved")||"[]");
let currentIndex=0,selected=null,practiceSet=[],practiceIndex=0,practiceAnswers={},practiceTimer=null,practiceSeconds=0;
let fontSize=100;
const $=id=>document.getElementById(id);
const persist=()=>{
 localStorage.setItem("prepify_answers",JSON.stringify(answers));
 localStorage.setItem("prepify_saved",JSON.stringify(saved));
};
function init(){
 if(!user){$("loginScreen").style.display="grid";$("app").style.display="none";return}
 $("loginScreen").style.display="none";$("app").style.display="flex";
 $("profileEmail").textContent=user;$("avatar").textContent=user[0].toUpperCase();
 $("dateLabel").textContent=new Date().toLocaleDateString("en-US",{weekday:"long",month:"long",day:"numeric"});
 if(!profile){$("setupModal").classList.add("show")}else{
  $("setupModal").classList.remove("show");renderDashboard();
 }
}
$("loginForm").addEventListener("submit",e=>{
 e.preventDefault();user=$("emailInput").value.trim().toLowerCase();
 if(!user)return;localStorage.setItem("prepify_email",user);profile=JSON.parse(localStorage.getItem("prepify_profile")||"null");init();
});
$("setupForm").addEventListener("submit",e=>{
 e.preventDefault();
 profile={targetMath:+$("targetMath").value,targetRW:+$("targetRW").value,dailyMath:+$("dailyMath").value,dailyRW:+$("dailyRW").value};
 localStorage.setItem("prepify_profile",JSON.stringify(profile));$("setupModal").classList.remove("show");renderDashboard();
});
function openSettings(){
 if(!profile)return;
 $("targetMath").value=profile.targetMath;$("targetRW").value=profile.targetRW;
 $("dailyMath").value=profile.dailyMath;$("dailyRW").value=profile.dailyRW;
 $("setupModal").classList.add("show");
}
$("logoutBtn").onclick=()=>{
 localStorage.removeItem("prepify_email");user="";profile=null;init();
};
$("themeBtn").onclick=$("themeTop").onclick=()=>{
 document.body.classList.toggle("dark");localStorage.setItem("prepify_theme",document.body.classList.contains("dark")?"dark":"light");
};
if(localStorage.getItem("prepify_theme")==="dark")document.body.classList.add("dark");
$("fontDown").onclick=()=>{fontSize=Math.max(85,fontSize-5);document.querySelector(".main").style.fontSize=fontSize+"%";};
$("fontUp").onclick=()=>{fontSize=Math.min(120,fontSize+5);document.querySelector(".main").style.fontSize=fontSize+"%";};
$("menuBtn").onclick=()=>$("sidebar").classList.toggle("open");

const pageNames={dashboard:"Dashboard",bank:"Question Bank",practice:"Practice Test",mistakes:"My Mistakes",data:"My Data",materials:"Study Materials"};
function showPage(name){
 document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
 $("page-"+name).classList.add("active");
 document.querySelectorAll(".nav-btn").forEach(b=>b.classList.remove("active"));
 const btn=document.querySelector('[data-page="'+name+'"]');if(btn)btn.classList.add("active");
 $("pageTitle").textContent=pageNames[name]||name;
 $("sidebar").classList.remove("open");
 if(name==="dashboard")renderDashboard();
 if(name==="bank")renderBank();
 if(name==="mistakes")renderMistakes();
 if(name==="data")renderData();
}
document.querySelectorAll("[data-page]").forEach(b=>b.onclick=()=>showPage(b.dataset.page));
document.querySelectorAll(".topic-link").forEach(b=>b.onclick=()=>{
 $("topicFilter").value=b.dataset.topic;showPage("bank");renderBank();
});
function getStats(){
 const vals=Object.values(answers),correct=vals.filter(x=>x.correct).length;
 return {total:vals.length,correct,wrong:vals.length-correct,accuracy:vals.length?Math.round(correct/vals.length*100):0};
}
function renderDashboard(){
 const s=getStats();
 $("statAnswered").textContent=s.total;$("statAccuracy").textContent=s.total?s.accuracy+"%":"—";
 $("statSaved").textContent=saved.length;$("statMistakes").textContent=s.wrong;
 const mathDone=Object.keys(answers).filter(id=>questions.find(q=>q.id==id)?.topic==="Math").length;
 const rwDone=s.total-mathDone;
 $("mathGoalText").textContent=mathDone+" / "+profile.dailyMath+" lessons";
 $("rwGoalText").textContent=rwDone+" / "+profile.dailyRW+" lessons";
 $("mathGoalBar").style.width=Math.min(100,mathDone/profile.dailyMath*100)+"%";
 $("rwGoalBar").style.width=Math.min(100,rwDone/profile.dailyRW*100)+"%";
 $("dashboardTopics").innerHTML=topics.map((t,i)=>`
 <div class="card course"><div class="course-icon">${["Aa","✎","⇄","✦"][i]}</div>
 <div style="flex:1"><b>${t}</b><p>${questions.filter(q=>q.topic===t).length} sample questions</p></div>
 <button class="secondary" onclick="chooseTopic('${t.replace(/'/g,"\\'")}')">Practice</button></div>`).join("");
}
function chooseTopic(t){$("topicFilter").value=t;showPage("bank");renderBank();}
function filteredQuestions(){
 const topic=$("topicFilter").value,status=$("statusFilter").value,search=$("searchInput").value.toLowerCase();
 return questions.filter(q=>{
  if(topic!=="All"&&q.topic!==topic)return false;
  if(status==="Unanswered"&&answers[q.id])return false;
  if(status==="Correct"&&!answers[q.id]?.correct)return false;
  if(status==="Wrong"&&(!answers[q.id]||answers[q.id].correct))return false;
  if(status==="Saved"&&!saved.includes(q.id))return false;
  return (q.text+" "+q.topic).toLowerCase().includes(search);
 });
}
function renderBank(){
 const list=filteredQuestions();
 $("bankProgress").textContent=Object.keys(answers).length+"/"+questions.length;
 $("bankProgressBar").style.width=(Object.keys(answers).length/questions.length*100)+"%";
 $("questionNav").innerHTML=list.map((q,i)=>`<button class="qnum ${i===currentIndex?"current":""} ${answers[q.id]?"done":""}" onclick="openQuestion(${q.id})">${i+1}</button>`).join("");
 if(!list.length){$("questionArea").innerHTML='<div class="empty">No questions match these filters.</div>';return}
 if(!list.some(q=>q.id===questions[currentIndex]?.id))currentIndex=questions.indexOf(list[0]);
 renderQuestion(questions[currentIndex]);
}
function openQuestion(id){currentIndex=questions.findIndex(q=>q.id===id);renderQuestion(questions[currentIndex]);}
function renderQuestion(q){
 if(!q)return;
 selected=null;
 const old=answers[q.id];
 $("questionArea").innerHTML=`
 <div class="q-top"><div class="q-meta"><span class="tag">${q.topic}</span><span class="muted">${q.difficulty}</span></div>
 <button class="icon-btn" onclick="toggleSave(${q.id})">${saved.includes(q.id)?"★ Saved":"☆ Save"}</button></div>
 <div class="muted">QUESTION ${questions.indexOf(q)+1} OF ${questions.length}</div>
 <div class="question-text">${q.text}</div>
 <div class="options">${q.options.map((o,i)=>`<div class="option ${old&&i===q.answer?"correct":""} ${old&&old.choice===i&&!old.correct?"wrong":""}" onclick="selectOption(${i})" data-option="${i}"><span class="option-letter">${"ABCD"[i]}</span><span>${o.replace(/^[A-D]\)\s*/,"")}</span></div>`).join("")}</div>
 <div id="feedback" class="feedback ${old?"show "+(old.correct?"good":"bad"):""}">${old?(old.correct?"Correct! ":"Not quite. ")+"<b>Answer: "+ "ABCD"[q.answer]+"</b><br>"+q.explanation:""}</div>
 <div class="q-actions"><button class="secondary" onclick="previousQuestion()">← Previous</button>
 <div style="display:flex;gap:8px"><button class="secondary" onclick="checkAnswer(${q.id})">Check answer</button><button class="primary" onclick="nextQuestion()">Next →</button></div></div>`;
}
function selectOption(i){
 selected=i;document.querySelectorAll(".option").forEach(o=>o.classList.toggle("selected",+o.dataset.option===i));
}
function checkAnswer(id){
 if(selected===null){alert("Please select an answer first.");return}
 const q=questions.find(x=>x.id===id),correct=selected===q.answer;
 answers[id]={choice:selected,correct};persist();renderQuestion(q);renderDashboard();
}
function toggleSave(id){
 saved=saved.includes(id)?saved.filter(x=>x!==id):[...saved,id];persist();renderQuestion(questions.find(q=>q.id===id));renderDashboard();
}
function nextQuestion(){
 const list=filteredQuestions();if(!list.length)return;
 const pos=list.findIndex(q=>q.id===questions[currentIndex]?.id);
 const next=list[(pos+1)%list.length];currentIndex=questions.indexOf(next);renderBank();
}
function previousQuestion(){
 const list=filteredQuestions();if(!list.length)return;
 const pos=list.findIndex(q=>q.id===questions[currentIndex]?.id);
 const prev=list[(pos-1+list.length)%list.length];currentIndex=questions.indexOf(prev);renderBank();
}
$("topicFilter").onchange=$("statusFilter").onchange=$("searchInput").oninput=()=>{currentIndex=0;renderBank()};
function renderMistakes(){
 const wrong=questions.filter(q=>answers[q.id]&&!answers[q.id].correct);
 $("mistakeList").innerHTML=wrong.length?wrong.map(q=>`
 <div class="topic-row"><div style="flex:1"><b>${q.topic}</b><small>${q.text.slice(0,110)}...</small></div>
 <button class="secondary" onclick="showPage('bank');openQuestion(${q.id})">Review</button></div>`).join(""):'<div class="empty">No mistakes yet. Answer some questions to build your review list.</div>';
}
function renderData(){
 const s=getStats();$("dataAnswered").textContent=s.total;$("dataCorrect").textContent=s.correct;
 $("dataWrong").textContent=s.wrong;$("dataAccuracy").textContent=s.total?s.accuracy+"%":"—";
 $("topicPerformance").innerHTML=topics.map(t=>{
  const qs=questions.filter(q=>q.topic===t),done=qs.filter(q=>answers[q.id]),correct=done.filter(q=>answers[q.id].correct).length;
  const pct=done.length?Math.round(correct/done.length*100):0;
  return `<div style="margin:17px 0"><div style="display:flex;justify-content:space-between;font-size:13px"><b>${t}</b><span class="muted">${done.length}/${qs.length} answered · ${done.length?pct+"% accuracy":"Not started"}</span></div><div class="progress"><span style="width:${pct}%"></span></div></div>`;
 }).join("");
}
function startPractice(){
 practiceSet=[...questions].sort(()=>Math.random()-.5).slice(0,5);
 practiceIndex=0;practiceAnswers={};practiceSeconds=0;
 $("practiceIntro").style.display="none";$("practiceArea").style.display="block";
 clearInterval(practiceTimer);practiceTimer=setInterval(()=>{practiceSeconds++;const el=$("practiceClock");if(el)el.textContent=formatTime(practiceSeconds)},1000);
 renderPracticeQuestion();
}
function formatTime(s){return Math.floor(s/60).toString().padStart(2,"0")+":"+ (s%60).toString().padStart(2,"0")}
function renderPracticeQuestion(){
 const q=practiceSet[practiceIndex];
 if(!q){finishPractice();return}
 $("practiceArea").innerHTML=`
 <div class="q-top"><span class="tag">QUESTION ${practiceIndex+1} / ${practiceSet.length}</span><b id="practiceClock"> ${formatTime(practiceSeconds)}</b></div>
 <div class="progress"><span style="width:${(practiceIndex+1)/practiceSet.length*100}%"></span></div>
 <div class="muted">${q.topic} · ${q.difficulty}</div><div class="question-text">${q.text}</div>
 <div class="options">${q.options.map((o,i)=>`<div class="option ${practiceAnswers[q.id]===i?"selected":""}" onclick="practiceSelect(${i})" data-option="${i}"><span class="option-letter">${"ABCD"[i]}</span><span>${o.replace(/^[A-D]\)\s*/,"")}</span></div>`).join("")}</div>
 <div class="q-actions"><button class="secondary" onclick="practicePrevious()" ${practiceIndex===0?"disabled":""}>Previous</button>
 <button class="primary" onclick="practiceNext()">${practiceIndex===practiceSet.length-1?"Finish test":"Next →"}</button></div>`;
}
function practiceSelect(i){practiceAnswers[practiceSet[practiceIndex].id]=i;renderPracticeQuestion();}
function practicePrevious(){if(practiceIndex>0){practiceIndex--;renderPracticeQuestion()}}
function practiceNext(){if(practiceIndex<practiceSet.length-1){practiceIndex++;renderPracticeQuestion()}else finishPractice()}
function finishPractice(){
 clearInterval(practiceTimer);
 const correct=practiceSet.filter(q=>practiceAnswers[q.id]===q.answer).length;
 $("practiceArea").innerHTML=`<div class="empty"><div style="font-size:35px">✓</div><h2>Practice completed!</h2><div class="stat-value">${correct} / ${practiceSet.length}</div><p class="muted">Correct answers · Time: ${formatTime(practiceSeconds)}</p><button class="primary" onclick="resetPractice()">Try another test</button></div>`;
 practiceSet.forEach(q=>{
  if(practiceAnswers[q.id]!==undefined){
   answers[q.id]={choice:practiceAnswers[q.id],correct:practiceAnswers[q.id]===q.answer};
  }
 });
 persist();renderDashboard();
}
function resetPractice(){$("practiceArea").style.display="none";$("practiceIntro").style.display="block"}
init();
</script>
</body>
</html>
