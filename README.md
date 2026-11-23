
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify | SAT Preparation</title>
<style>
:root{
 --bg:#f5f7fc;--panel:#fff;--text:#17213a;--muted:#78849b;
 --line:#e6eaf2;--primary:#6256e8;--soft:#f0efff;
 --green:#159b72;--red:#df5968;
}
body.dark{--bg:#111522;--panel:#1b2232;--text:#edf0fa;--muted:#9ba6bb;--line:#30394c;--primary:#9288ff;--soft:#292644}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Arial,sans-serif}
button,input,select{font:inherit}
button{cursor:pointer}
.app{display:flex;min-height:100vh}
.sidebar{width:250px;position:fixed;inset:0 auto 0 0;background:var(--panel);border-right:1px solid var(--line);padding:22px 15px;display:flex;flex-direction:column;z-index:10;overflow:auto}
.logo{font-size:23px;font-weight:800;display:flex;align-items:center;gap:10px;padding:0 10px 28px}
.logo-icon{background:var(--primary);color:white;border-radius:10px;width:35px;height:35px;display:grid;place-items:center}
.nav-label{font-size:10px;font-weight:800;letter-spacing:1.5px;color:var(--muted);padding:13px 12px 7px}
.nav-btn{display:block;width:100%;text-align:left;padding:13px 12px;border:0;border-radius:9px;background:transparent;color:var(--muted);font-size:13px;font-weight:650;margin:2px 0}
.nav-btn:hover,.nav-btn.active{background:var(--soft);color:var(--primary)}
.sidebar-bottom{margin-top:auto;border-top:1px solid var(--line);padding-top:12px}
.profile{padding:12px;font-size:12px;overflow-wrap:anywhere}
.profile small{display:block;color:var(--muted);margin-top:5px}
.main{margin-left:250px;width:calc(100% - 250px);padding:30px 35px 60px}
.topbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:25px}
h1{font-size:28px;margin:0}h2{font-size:19px;margin:0 0 13px}h3{font-size:15px;margin:0 0 9px}
.muted{color:var(--muted);font-size:12px;line-height:1.6}
.eyebrow{font-size:11px;color:var(--muted);margin-bottom:7px}
.card{background:var(--panel);border:1px solid var(--line);border-radius:14px;padding:21px}
.grid{display:grid;gap:15px}
.stats{grid-template-columns:repeat(4,minmax(0,1fr));margin-bottom:17px}
.stat-label{font-size:12px;color:var(--muted)}
.stat-value{font-size:27px;font-weight:800;margin:10px 0}
.progress{height:7px;background:var(--line);border-radius:20px;overflow:hidden;margin:12px 0}
.progress span{display:block;height:100%;background:var(--primary)}
.primary,.secondary,.icon-btn{border-radius:9px;padding:11px 15px;font-weight:650}
.primary{background:var(--primary);color:white;border:0}
.secondary,.icon-btn{background:var(--panel);border:1px solid var(--line);color:var(--text)}
.page{display:none}.page.active{display:block}
.welcome{background:linear-gradient(120deg,#5147ce,#887df8);color:white;border:0;padding:28px;margin-bottom:18px}
.welcome p{font-size:13px;line-height:1.7;max-width:600px}
.welcome .primary{background:white;color:#5147ce}
.dashboard-grid{grid-template-columns:1.3fr 1fr}
.topic-grid{grid-template-columns:repeat(2,minmax(0,1fr))}
.topic-card{display:flex;justify-content:space-between;align-items:center;gap:12px}
.topic-card p{font-size:12px;color:var(--muted);margin:5px 0}
.tag{background:var(--soft);color:var(--primary);font-size:10px;font-weight:750;padding:6px 9px;border-radius:20px}
.filters{display:flex;gap:10px;flex-wrap:wrap;margin:18px 0}
.filters input,.filters select,.modal input{background:var(--panel);color:var(--text);border:1px solid var(--line);padding:12px;border-radius:9px}
.filters input{flex:1;min-width:190px}
.list{display:grid;gap:10px}
.list-item{border:1px solid var(--line);padding:14px;border-radius:10px;display:flex;align-items:center;justify-content:space-between;gap:10px}
.page-heading{display:flex;justify-content:space-between;align-items:center;gap:12px}
.empty{text-align:center;color:var(--muted);padding:45px 15px}
.modal-bg{display:none;position:fixed;inset:0;background:#080d1acc;z-index:50;place-items:center;padding:20px}
.modal-bg.show{display:grid}
.modal{width:min(480px,100%);background:var(--panel);padding:27px;border-radius:16px}
.modal input{display:block;width:100%;margin:8px 0 15px}
.modal label{font-size:12px;color:var(--muted)}
.login-screen{min-height:100vh;display:grid;place-items:center;padding:20px}
.login-box{width:min(420px,100%);padding:35px;background:var(--panel);border:1px solid var(--line);border-radius:17px}
.login-box input{width:100%;padding:13px;border:1px solid var(--line);border-radius:9px;background:var(--bg);color:var(--text);margin:9px 0 15px}
.login-box .primary{width:100%}

/* Question Bank full-width practice */
.bank-intro{padding:28px;margin-bottom:18px}
.bank-intro h2{font-size:24px}
.bank-topics{grid-template-columns:repeat(2,minmax(0,1fr))}
.bank-topic{padding:22px}
.bank-topic .topic-description{color:var(--muted);font-size:12px;line-height:1.6;margin:8px 0 17px}
.bank-topic-footer{display:flex;justify-content:space-between;align-items:center;gap:10px}
.bank-list{display:grid;gap:12px}
.bank-question{padding:20px}
.bank-question-title{font-weight:700;margin-bottom:9px}
.bank-question-sub{font-size:12px;color:var(--muted)}
.bank-question-actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:15px}

/* Full screen exam */
.exam{display:none;position:fixed;inset:0;z-index:100;background:var(--bg);color:var(--text);overflow:auto}
.exam.active{display:flex;flex-direction:column}
.exam-header{height:68px;background:var(--panel);border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;padding:0 4%;flex-shrink:0;gap:12px}
.exam-logo{font-size:19px;font-weight:800;display:flex;align-items:center;gap:9px}
.exam-header-right{display:flex;align-items:center;gap:15px}
.clock{font-size:22px;font-weight:800;font-variant-numeric:tabular-nums;min-width:75px;text-align:center}
.clock.warning{color:var(--red)}
.exam-body{width:100%;max-width:1200px;margin:0 auto;padding:35px 5% 125px;flex:1}
.exam-progress{height:5px;background:var(--line);border-radius:10px;margin:17px 0 28px}
.exam-progress span{display:block;height:100%;background:var(--primary)}
.exam-headline{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}
.exam-question-label{font-size:13px;font-weight:700;color:var(--muted)}
.exam-question-text{font-size:21px;line-height:1.75;white-space:pre-line;margin:30px 0}
.exam-choices{display:grid;gap:13px;max-width:1000px}
.choice{display:flex;align-items:flex-start;gap:13px;padding:17px;border:1px solid var(--line);border-radius:11px;background:var(--panel);cursor:pointer;font-size:16px;line-height:1.6}
.choice:hover{border-color:var(--primary)}
.choice.selected{background:var(--soft);border:2px solid var(--primary);padding:16px}
.choice-letter{width:29px;height:29px;border-radius:8px;background:var(--bg);display:grid;place-items:center;font-weight:800;flex-shrink:0}
.exam-footer{position:fixed;bottom:0;left:0;right:0;z-index:5;background:var(--panel);border-top:1px solid var(--line);padding:14px 4%;display:flex;justify-content:space-between;align-items:center;gap:12px}
.footer-group{display:flex;align-items:center;gap:10px}
.exam-navigator{display:none;background:var(--panel);border:1px solid var(--line);border-radius:12px;padding:17px;margin-top:20px}
.exam-navigator.show{display:block}
.navigator-grid{display:grid;grid-template-columns:repeat(10,1fr);gap:8px;margin-top:12px}
.navigator-grid button{border:1px solid var(--line);background:var(--bg);color:var(--text);padding:10px;border-radius:8px}
.navigator-grid button.current{border:2px solid var(--primary);color:var(--primary)}
.navigator-grid button.answered{background:#159b7218;border-color:#159b7277}
.navigator-grid button.flagged{outline:2px solid var(--red)}
.exam-setup{max-width:700px;margin:35px auto;background:var(--panel);border:1px solid var(--line);border-radius:17px;padding:35px}
.exam-setup h1{font-size:29px;margin-bottom:12px}
.mode-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin:18px 0}
.mode-option{border:2px solid var(--line);border-radius:12px;padding:18px;cursor:pointer}
.mode-option.active{border-color:var(--primary);background:var(--soft)}
.mode-option b{display:block;margin-bottom:7px}
.mode-option p{font-size:12px;color:var(--muted);line-height:1.6;margin:0}
.exam-setup select{width:100%;padding:12px;border:1px solid var(--line);border-radius:9px;background:var(--bg);color:var(--text);margin:8px 0 18px}
.exam-result{text-align:center;padding:45px 20px}
.exam-result .score{font-size:58px;font-weight:850;margin:20px 0}
.result-stats{display:flex;justify-content:center;gap:35px;flex-wrap:wrap;margin:25px}
.result-stats b{display:block;font-size:22px;margin-bottom:5px}
@media(max-width:900px){.stats{grid-template-columns:repeat(2,1fr)}.dashboard-grid{grid-template-columns:1fr}}
@media(max-width:650px){
 .sidebar{transform:translateX(-100%);transition:.2s}.sidebar.open{transform:translateX(0)}
 .main{margin:0;width:100%;padding:18px 13px}
 .bank-topics,.topic-grid{grid-template-columns:1fr}
 .exam-header{padding:0 12px;height:60px}
 .exam-body{padding:22px 15px 115px}
 .exam-question-text{font-size:18px;margin:22px 0}
 .exam-footer{padding:11px}
 .exam-footer .muted{display:none}
 .navigator-grid{grid-template-columns:repeat(5,1fr)}
 .exam-setup{padding:22px;margin:15px}
 .mode-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<div class="login-screen" id="loginScreen">
 <div class="login-box">
  <div class="logo"><span class="logo-icon">P</span> Prepify</div>
  <p class="muted">Your personal SAT preparation platform.</p>
  <h1 style="font-size:26px">Welcome back!</h1>
  <form id="loginForm">
   <label>Email address</label>
   <input type="email" id="emailInput" placeholder="you@example.com" required>
   <button class="primary">Continue with email →</button>
  </form>
  <p class="muted">Prototype login. Real email verification requires a backend.</p>
 </div>
</div>

<div class="app" id="app" style="display:none">
 <aside class="sidebar" id="sidebar">
  <div class="logo"><span class="logo-icon">P</span> Prepify</div>
  <div class="nav-label">STUDY</div>
  <button class="nav-btn active" data-page="dashboard">▦ Dashboard</button>
  <button class="nav-btn" data-page="bank">▤ Question Bank</button>
  <button class="nav-btn" data-page="practice">◷ Practice Test</button>
  <button class="nav-btn" data-page="mistakes">↻ My Mistakes</button>
  <button class="nav-btn" data-page="data">▥ My Data</button>
  <button class="nav-btn" data-page="materials">▧ Study Materials</button>
  <div class="nav-label">READING & WRITING</div>
  <button class="nav-btn topic-link" data-topic="Boundaries">A Boundaries</button>
  <button class="nav-btn topic-link" data-topic="Form, Structure & Sense">A Form, Structure & Sense</button>
  <button class="nav-btn topic-link" data-topic="Transitions">A Transitions</button>
  <button class="nav-btn topic-link" data-topic="Rhetorical Synthesis">A Rhetorical Synthesis</button>
  <div class="sidebar-bottom">
   <button class="nav-btn" id="themeBtn">◐ Toggle theme</button>
   <button class="nav-btn" id="logoutBtn">⇥ Log out</button>
   <div class="profile"><b id="profileEmail">Student</b><small>Prepify student</small></div>
  </div>
 </aside>

 <main class="main">
  <div class="topbar">
   <div><div class="eyebrow">YOUR STUDY SPACE</div><h1 id="pageTitle">Dashboard</h1></div>
   <button class="icon-btn" id="mobileMenu">☰</button>
  </div>

  <section class="page active" id="page-dashboard">
   <div class="card welcome">
    <div class="eyebrow" style="color:#e3e0ff">YOUR PERSONAL SAT WORKSPACE</div>
    <h2 style="font-size:27px">Make every practice count.</h2>
    <p>Improve your SAT skills, practice by topic, and track your progress.</p>
    <button class="primary" onclick="showPage('bank')">Open Question Bank →</button>
   </div>
   <div class="grid stats">
    <div class="card"><div class="stat-label">Questions answered</div><div class="stat-value" id="statAnswered">0</div></div>
    <div class="card"><div class="stat-label">Accuracy</div><div class="stat-value" id="statAccuracy">—</div></div>
    <div class="card"><div class="stat-label">Saved questions</div><div class="stat-value" id="statSaved">0</div></div>
    <div class="card"><div class="stat-label">Mistakes</div><div class="stat-value" id="statMistakes">0</div></div>
   </div>
   <div class="grid dashboard-grid">
    <div class="card"><h2>Your progress</h2><div class="muted">Overall question completion</div><div class="progress"><span id="overallProgress" style="width:0%"></span></div><div class="muted" id="overallText">0 of 8 questions answered</div></div>
    <div class="card"><h2>Quick access</h2><div class="list">
     <div class="list-item"><b>Question Bank</b><button class="secondary" onclick="showPage('bank')">Open</button></div>
     <div class="list-item"><b>Practice Test</b><button class="secondary" onclick="showPage('practice')">Open</button></div>
    </div></div>
   </div>
   <div style="margin:25px 0 13px"><h2>Reading & Writing skills</h2></div>
   <div class="grid topic-grid" id="dashboardTopics"></div>
  </section>

  <section class="page" id="page-bank">
   <div class="card bank-intro">
    <div class="eyebrow">READING & WRITING</div>
    <h2>Question Bank</h2>
    <p class="muted">Choose a skill first. Questions will not appear until you start a practice session.</p>
   </div>
   <div class="filters">
    <input id="bankSearch" placeholder="Search skills...">
    <select id="bankStatus"><option value="All">All questions</option><option value="Unanswered">Not answered</option><option value="Correct">Correct</option><option value="Wrong">Incorrect</option><option value="Saved">Saved</option></select>
   </div>
   <div class="grid bank-topics" id="bankTopics"></div>
   <div id="bankResults" style="display:none;margin-top:22px">
    <div class="page-heading" style="margin-bottom:15px">
     <div><div class="eyebrow">SELECTED SKILL</div><h2 id="selectedTopicTitle"></h2><p class="muted" id="selectedTopicCount"></p></div>
     <button class="secondary" onclick="backToTopics()">← All skills</button>
    </div>
    <div class="bank-list" id="bankQuestionList"></div>
   </div>
  </section>

  <section class="page" id="page-practice">
   <div class="card">
    <div class="eyebrow">EXAM SIMULATION</div>
    <h2>Practice Test</h2>
    <p class="muted">Start a full-screen SAT-style practice session. Choose a timer or untimed mode before beginning.</p>
    <div class="grid stats" style="grid-template-columns:repeat(3,1fr);margin:22px 0">
     <div class="card"><div class="stat-label">Sample questions</div><div class="stat-value">8</div></div>
     <div class="card"><div class="stat-label">Sections</div><div class="stat-value">4</div></div>
     <div class="card"><div class="stat-label">Display</div><div class="stat-value" style="font-size:20px">Full screen</div></div>
    </div>
    <button class="primary" onclick="launchExam('all')">Set up full practice test →</button>
   </div>
  </section>

  <section class="page" id="page-mistakes">
   <div class="card"><h2>My Mistakes</h2><p class="muted">Review your incorrect answers.</p><div id="mistakesList"></div></div>
  </section>
  <section class="page" id="page-data">
   <div class="card"><h2>My Data</h2><div class="grid stats" style="margin-top:20px">
    <div><div class="stat-label">Answered</div><div class="stat-value" id="dataAnswered">0</div></div>
    <div><div class="stat-label">Correct</div><div class="stat-value" id="dataCorrect">0</div></div>
    <div><div class="stat-label">Incorrect</div><div class="stat-value" id="dataWrong">0</div></div>
    <div><div class="stat-label">Accuracy</div><div class="stat-value" id="dataAccuracy">—</div></div>
   </div><div id="topicStats"></div></div>
  </section>
  <section class="page" id="page-materials">
   <div class="card"><h2>Study Materials</h2><div class="list">
    <div class="list-item"><div><b>College Board SAT</b><p class="muted">Official SAT information</p></div><a href="https://satsuite.collegeboard.org/" target="_blank">Open ↗</a></div>
    <div class="list-item"><div><b>Bluebook</b><p class="muted">Official testing application</p></div><a href="https://bluebook.collegeboard.org/" target="_blank">Open ↗</a></div>
    <div class="list-item"><div><b>Khan Academy</b><p class="muted">Free SAT preparation</p></div><a href="https://www.khanacademy.org/test-prep/sat" target="_blank">Open ↗</a></div>
    <div class="list-item"><div><b>College Board Question Bank</b><p class="muted">Official practice questions</p></div><a href="https://satsuitequestionbank.collegeboard.org/" target="_blank">Open ↗</a></div>
   </div></div>
  </section>
 </main>
</div>

<!-- Exam screen -->
<div class="exam" id="exam">
 <header class="exam-header">
  <div class="exam-logo"><span class="logo-icon">P</span> Prepify <span class="muted">| Exam</span></div>
  <div class="exam-header-right">
   <span class="muted" id="examModeLabel">TIMED</span>
   <div class="clock" id="clock">32:00</div>
   <button class="icon-btn" onclick="toggleFullscreen()">⛶</button>
   <button class="icon-btn" onclick="leaveExam()">✕</button>
  </div>
 </header>

 <div class="exam-body">
  <div id="examSetup">
   <div class="exam-setup">
    <div class="eyebrow">PREPIFY TESTING ENVIRONMENT</div>
    <h1>Set up your practice</h1>
    <p class="muted">Choose your testing mode. Questions will appear only after you press Start Exam.</p>
    <h3 style="margin-top:25px">Select mode</h3>
    <div class="mode-grid">
     <div class="mode-option active" id="timedOption" onclick="setMode('timed')">
      <b>◷ Timed</b><p>Practice under time pressure with a countdown timer.</p>
     </div>
     <div class="mode-option" id="untimedOption" onclick="setMode('untimed')">
      <b>∞ Untimed</b><p>Take as much time as you need. No countdown.</p>
     </div>
    </div>
    <div id="durationArea">
     <label class="muted">Time limit</label>
     <select id="duration">
      <option value="10">10 minutes</option>
      <option value="20">20 minutes</option>
      <option value="32" selected>32 minutes</option>
      <option value="35">35 minutes</option>
     </select>
    </div>
    <div class="list-item" style="margin:15px 0">
     <div><b id="examScopeTitle">All Reading & Writing skills</b><p class="muted" id="examScopeDesc">8 sample questions</p></div>
     <span class="tag" id="examCount">8 QUESTIONS</span>
    </div>
    <button class="primary" style="width:100%;padding:15px" onclick="startExam()">Start Exam →</button>
   </div>
  </div>

  <div id="examWork" style="display:none">
   <div class="exam-headline">
    <span class="exam-question-label" id="examQuestionNumber">QUESTION 1 OF 8</span>
    <button class="secondary" id="flagBtn" onclick="toggleFlag()">⚑ Mark for review</button>
   </div>
   <div class="exam-progress"><span id="examProgressBar" style="width:12.5%"></span></div>
   <div class="muted" id="examTopic"></div>
   <div class="exam-question-text" id="examQuestionText"></div>
   <div class="exam-choices" id="examChoices"></div>
   <div class="exam-navigator" id="examNavigator">
    <b>Question navigator</b><p class="muted">Choose a question number to move to it.</p>
    <div class="navigator-grid" id="navigatorGrid"></div>
   </div>
  </div>

  <div id="examResults" style="display:none"></div>
 </div>

 <footer class="exam-footer" id="examFooter" style="display:none">
  <div class="footer-group">
   <button class="secondary" onclick="toggleNavigator()">☷ Questions</button>
   <span class="muted" id="answeredCounter">0 of 8 answered</span>
  </div>
  <div class="footer-group">
   <button class="secondary" id="prevBtn" onclick="examPrevious()">← Back</button>
   <button class="primary" id="nextBtn" onclick="examNext()">Next →</button>
   <button class="primary" id="submitBtn" onclick="confirmSubmit()" style="display:none">Submit Test</button>
  </div>
 </footer>
</div>

<script>
const topics=["Boundaries","Form, Structure & Sense","Transitions","Rhetorical Synthesis"];
const questions=[
{id:1,topic:topics[0],difficulty:"Medium",text:"The research team collected data from several coastal regions ____ the results revealed a clear pattern in water temperature.",options:["regions, and the","regions; the","regions the","regions, the"],answer:1,explanation:"The sentence contains two independent clauses. A semicolon can join two closely related independent clauses."},
{id:2,topic:topics[0],difficulty:"Medium",text:"Although the experiment was initially considered unsuccessful ____ the researchers later discovered an important result.",options:["unsuccessful,","unsuccessful;","unsuccessful","unsuccessful:"],answer:0,explanation:"An introductory dependent clause beginning with “Although” is followed by a comma."},
{id:3,topic:topics[1],difficulty:"Medium",text:"The collection of rare plants ____ carefully maintained by the university's biology department.",options:["are","were","is","have been"],answer:2,explanation:"The subject “collection” is singular, so the singular verb “is” is correct."},
{id:4,topic:topics[1],difficulty:"Hard",text:"By the time the final report was published, the scientists ____ the data for nearly three years.",options:["analyze","had been analyzing","will analyze","are analyzing"],answer:1,explanation:"The past perfect progressive describes an activity continuing before another past event."},
{id:5,topic:topics[2],difficulty:"Medium",text:"The first design was inexpensive to produce. ____, it required frequent repairs, making it costly over time.",options:["For example","Nevertheless","Similarly","In addition"],answer:1,explanation:"“Nevertheless” introduces a contrast between the low initial cost and later repair expenses."},
{id:6,topic:topics[2],difficulty:"Hard",text:"Several studies have examined the effects of urban green spaces on air quality. ____, recent research has also explored their influence on residents' mental well-being.",options:["In contrast","As a result","Furthermore","Instead"],answer:2,explanation:"“Furthermore” adds another related point."},
{id:7,topic:topics[3],difficulty:"Medium",text:"A student is writing about a museum exhibition. The student wants to emphasize that the exhibition includes works from different historical periods.\n\nNotes:\n• The exhibition opened in 2024.\n• It contains 60 paintings.\n• The paintings were created between 1600 and 1950.\n• The exhibition is located in the city art museum.\n\nWhich choice most effectively uses the notes to achieve the student's goal?",options:["The city art museum opened an exhibition in 2024.","The exhibition features 60 paintings created across a period spanning from 1600 to 1950.","The museum is located in the city center.","Sixty paintings are included in the exhibition."],answer:1,explanation:"This choice emphasizes the different historical periods represented by the paintings."},
{id:8,topic:topics[3],difficulty:"Hard",text:"A student is writing about a scientific discovery. The student wants to compare the two methods used in the study.\n\nNotes:\n• Method A took 12 hours to complete.\n• Method B took 4 hours to complete.\n• Both methods produced results with similar accuracy.\n\nWhich choice best achieves the student's goal?",options:["The study used two methods to collect scientific data.","Method A and Method B both produced accurate results.","Although Method A took longer, both methods achieved similar levels of accuracy.","Method B was used in a scientific study."],answer:2,explanation:"This choice compares the time required by each method while highlighting their similar accuracy."}
];

const $=id=>document.getElementById(id);
let user=localStorage.getItem("prepify_email")||"";
let answers=JSON.parse(localStorage.getItem("prepify_answers")||"{}");
let saved=JSON.parse(localStorage.getItem("prepify_saved")||"[]");
let selectedTopic="All",mode="timed",examQuestions=[],examAnswers={},flags=[],examIndex=0,seconds=0,timer=null,examRunning=false;

function save(){
 localStorage.setItem("prepify_answers",JSON.stringify(answers));
 localStorage.setItem("prepify_saved",JSON.stringify(saved));
}
function init(){
 if(!user){$("loginScreen").style.display="grid";$("app").style.display="none";return}
 $("loginScreen").style.display="none";$("app").style.display="flex";
 $("profileEmail").textContent=user;renderDashboard();
}
$("loginForm").onsubmit=e=>{
 e.preventDefault();user=$("emailInput").value.trim().toLowerCase();
 localStorage.setItem("prepify_email",user);init();
};
$("logoutBtn").onclick=()=>{
 localStorage.removeItem("prepify_email");user="";init();
};
$("themeBtn").onclick=()=>{
 document.body.classList.toggle("dark");
 localStorage.setItem("prepify_theme",document.body.classList.contains("dark")?"dark":"light");
};
if(localStorage.getItem("prepify_theme")==="dark")document.body.classList.add("dark");
$("mobileMenu").onclick=()=>$("sidebar").classList.toggle("open");

const pageNames={dashboard:"Dashboard",bank:"Question Bank",practice:"Practice Test",mistakes:"My Mistakes",data:"My Data",materials:"Study Materials"};
function showPage(name){
 document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
 $("page-"+name).classList.add("active");
 document.querySelectorAll("[data-page]").forEach(b=>b.classList.toggle("active",b.dataset.page===name));
 $("pageTitle").textContent=pageNames[name];$("sidebar").classList.remove("open");
 if(name==="bank")backToTopics();
 if(name==="dashboard")renderDashboard();
 if(name==="mistakes")renderMistakes();
 if(name==="data")renderData();
}
document.querySelectorAll("[data-page]").forEach(b=>b.onclick=()=>showPage(b.dataset.page));
document.querySelectorAll(".topic-link").forEach(b=>b.onclick=()=>{
 showPage("bank");selectTopic(b.dataset.topic);
});

function stats(){
 const list=Object.values(answers),correct=list.filter(a=>a.correct).length;
 return {total:list.length,correct,wrong:list.length-correct,accuracy:list.length?Math.round(correct/list.length*100):0};
}
function renderDashboard(){
 const s=stats();
 $("statAnswered").textContent=s.total;$("statAccuracy").textContent=s.total?s.accuracy+"%":"—";
 $("statSaved").textContent=saved.length;$("statMistakes").textContent=s.wrong;
 $("overallProgress").style.width=s.total/questions.length*100+"%";
 $("overallText").textContent=s.total+" of "+questions.length+" questions answered";
 $("dashboardTopics").innerHTML=topics.map((t,i)=>`
 <div class="card topic-card"><div><b>${t}</b><p>${questions.filter(q=>q.topic===t).length} sample questions</p></div>
 <button class="secondary" onclick="showPage('bank');selectTopic('${t}')">Open</button></div>`).join("");
}
function backToTopics(){
 selectedTopic="All";$("bankTopics").style.display="grid";$("bankResults").style.display="none";
 $("bankSearch").value="";$("bankStatus").value="All";renderTopicCards();
}
function renderTopicCards(){
 const search=$("bankSearch").value.toLowerCase();
 const status=$("bankStatus").value;
 const visible=topics.filter(t=>t.toLowerCase().includes(search));
 $("bankTopics").innerHTML=visible.map(t=>{
  const qs=questions.filter(q=>q.topic===t);
  let filtered=filterStatus(qs,status);
  return `<div class="card bank-topic"><div class="eyebrow">READING & WRITING</div><h2>${t}</h2>
   <div class="topic-description">Practice this skill with focused questions. Your progress is saved as you work.</div>
   <div class="bank-topic-footer"><span class="muted">${filtered.length} questions available</span><button class="primary" onclick="selectTopic('${t}')">Start Practice →</button></div></div>`;
 }).join("")||'<div class="empty">No skills found.</div>';
}
function filterStatus(qs,status){
 if(status==="Unanswered")return qs.filter(q=>!answers[q.id]);
 if(status==="Correct")return qs.filter(q=>answers[q.id]?.correct);
 if(status==="Wrong")return qs.filter(q=>answers[q.id]&&!answers[q.id].correct);
 if(status==="Saved")return qs.filter(q=>saved.includes(q.id));
 return qs;
}
function selectTopic(topic){
 selectedTopic=topic;
 $("bankTopics").style.display="none";$("bankResults").style.display="block";
 $("selectedTopicTitle").textContent=topic;
 const qs=filterStatus(questions.filter(q=>q.topic===topic),$("bankStatus").value);
 $("selectedTopicCount").textContent=qs.length+" questions in this skill";
 $("bankQuestionList").innerHTML=qs.map((q,i)=>`
 <div class="card bank-question">
  <div class="bank-question-title">Question ${i+1}</div>
  <div class="bank-question-sub">${q.difficulty} · ${answers[q.id]?(answers[q.id].correct?"Correct":"Incorrect"):"Not answered"}</div>
  <div class="bank-question-actions">
   <button class="primary" onclick="launchExam('${topic}',${q.id})">Start Practice →</button>
   <button class="secondary" onclick="toggleSave(${q.id})">${saved.includes(q.id)?"★ Saved":"☆ Save"}</button>
  </div>
 </div>`).join("")||'<div class="empty">No questions match this filter.</div>';
}
$("bankSearch").oninput=()=>{if(selectedTopic==="All")renderTopicCards()};
$("bankStatus").onchange=()=>{if(selectedTopic==="All")renderTopicCards();else selectTopic(selectedTopic)};
function toggleSave(id){
 saved=saved.includes(id)?saved.filter(x=>x!==id):[...saved,id];save();
 if(selectedTopic!=="All")selectTopic(selectedTopic);
 renderDashboard();
}

/* Exam setup and modes */
function launchExam(scope,oneId=null){
 examQuestions=oneId?questions.filter(q=>q.id===oneId):scope==="all"?[...questions]:questions.filter(q=>q.topic===scope);
 if(!examQuestions.length)return;
 $("exam").classList.add("active");
 $("examSetup").style.display="block";$("examWork").style.display="none";
 $("examResults").style.display="none";$("examFooter").style.display="none";
 $("examScopeTitle").textContent=scope==="all"?"All Reading & Writing skills":scope;
 $("examScopeDesc").textContent=examQuestions.length+" question(s) in this practice session";
 $("examCount").textContent=examQuestions.length+" QUESTIONS";
 mode="timed";setMode("timed");
 $("examNavigator").classList.remove("show");
 examRunning=false;
}
function setMode(value){
 mode=value;
 $("timedOption").classList.toggle("active",value==="timed");
 $("untimedOption").classList.toggle("active",value==="untimed");
 $("durationArea").style.display=value==="timed"?"block":"none";
}
function startExam(){
 examIndex=0;examAnswers={};flags=[];examRunning=true;
 seconds=Number($("duration").value)*60;
 $("examSetup").style.display="none";$("examWork").style.display="block";
 $("examResults").style.display="none";$("examFooter").style.display="flex";
 $("examModeLabel").textContent=mode==="timed"?"TIMED":"UNTIMED";
 if(mode==="timed"){
  updateClock();clearInterval(timer);
  timer=setInterval(()=>{
   seconds--;updateClock();
   if(seconds<=0){clearInterval(timer);finishExam(true)}
  },1000);
 }else{$("clock").textContent="∞";$("clock").classList.remove("warning")}
 renderExamQuestion();
 if(!document.fullscreenElement)document.documentElement.requestFullscreen?.().catch(()=>{});
}
function updateClock(){
 $("clock").textContent=String(Math.floor(seconds/60)).padStart(2,"0")+":"+String(seconds%60).padStart(2,"0");
 $("clock").classList.toggle("warning",seconds<=300);
}
function renderExamQuestion(){
 const q=examQuestions[examIndex];
 $("examQuestionNumber").textContent="QUESTION "+(examIndex+1)+" OF "+examQuestions.length;
 $("examProgressBar").style.width=(examIndex+1)/examQuestions.length*100+"%";
 $("examTopic").textContent=q.topic+" · "+q.difficulty;
 $("examQuestionText").textContent=q.text;
 $("examChoices").innerHTML=q.options.map((o,i)=>`
 <div class="choice ${examAnswers[q.id]===i?"selected":""}" onclick="chooseExamAnswer(${i})">
 <span class="choice-letter">${"ABCD"[i]}</span><span>${o}</span></div>`).join("");
 $("flagBtn").textContent=flags.includes(q.id)?"⚑ Marked for review":"⚑ Mark for review";
 $("prevBtn").disabled=examIndex===0;
 $("nextBtn").style.display=examIndex===examQuestions.length-1?"none":"inline-block";
 $("submitBtn").style.display=examIndex===examQuestions.length-1?"inline-block":"none";
 $("answeredCounter").textContent=Object.keys(examAnswers).length+" of "+examQuestions.length+" answered";
 renderNavigator();
}
function chooseExamAnswer(i){examAnswers[examQuestions[examIndex].id]=i;renderExamQuestion()}
function examPrevious(){if(examIndex>0){examIndex--;renderExamQuestion()}}
function examNext(){if(examIndex<examQuestions.length-1){examIndex++;renderExamQuestion()}}
function toggleFlag(){
 const id=examQuestions[examIndex].id;
 flags=flags.includes(id)?flags.filter(x=>x!==id):[...flags,id];
 renderExamQuestion();
}
function toggleNavigator(){$("examNavigator").classList.toggle("show")}
function renderNavigator(){
 $("navigatorGrid").innerHTML=examQuestions.map((q,i)=>`
 <button class="${i===examIndex?"current ":""}${examAnswers[q.id]!==undefined?"answered ":""}${flags.includes(q.id)?"flagged":""}" onclick="goToExamQuestion(${i})">${i+1}</button>`).join("");
}
function goToExamQuestion(i){examIndex=i;renderExamQuestion();$("examNavigator").classList.remove("show")}
function confirmSubmit(){
 const unanswered=examQuestions.filter(q=>examAnswers[q.id]===undefined).length;
 if(confirm(unanswered?`You have ${unanswered} unanswered question(s). Submit anyway?`:"Submit your test now?"))finishExam(false);
}
function finishExam(timeUp){
 clearInterval(timer);
 examQuestions.forEach(q=>{
  if(examAnswers[q.id]!==undefined)answers[q.id]={choice:examAnswers[q.id],correct:examAnswers[q.id]===q.answer};
 });
 save();examRunning=false;
 const correct=examQuestions.filter(q=>examAnswers[q.id]===q.answer).length;
 const attempted=Object.keys(examAnswers).length;
 $("examWork").style.display="none";$("examFooter").style.display="none";$("examResults").style.display="block";
 $("examResults").innerHTML=`
 <div class="exam-setup exam-result">
  <div class="eyebrow">${timeUp?"TIME IS UP":"TEST SUBMITTED"}</div>
  <h1>Practice completed!</h1>
  <div class="score">${correct}/${examQuestions.length}</div>
  <p class="muted">${Math.round(correct/examQuestions.length*100)}% correct</p>
  <div class="result-stats">
   <div><b>${attempted}</b><span class="muted">Answered</span></div>
   <div><b>${examQuestions.length-attempted}</b><span class="muted">Unanswered</span></div>
   <div><b>${examQuestions.length-correct}</b><span class="muted">Incorrect</span></div>
  </div>
  <p class="muted">This is a Prepify sample-test result, not an official SAT score.</p>
  <button class="primary" onclick="reviewExam()">Review answers</button>
  <button class="secondary" onclick="closeExam()">Back to Prepify</button>
 </div>`;
 renderDashboard();
}
function reviewExam(){
 $("examResults").style.display="none";$("examWork").style.display="block";$("examFooter").style.display="flex";
 examIndex=0;renderReviewQuestion();
}
function renderReviewQuestion(){
 const q=examQuestions[examIndex];
 $("examQuestionNumber").textContent="REVIEW · QUESTION "+(examIndex+1)+" OF "+examQuestions.length;
 $("examProgressBar").style.width=(examIndex+1)/examQuestions.length*100+"%";
 $("examTopic").textContent=q.topic+" · "+(examAnswers[q.id]===q.answer?"Correct":"Incorrect / unanswered");
 $("examQuestionText").textContent=q.text;
 $("examChoices").innerHTML=q.options.map((o,i)=>`
 <div class="choice" style="${i===q.answer?"border-color:var(--green);background:#159b7215":examAnswers[q.id]===i?"border-color:var(--red);background:#df596815":""}">
 <span class="choice-letter">${"ABCD"[i]}</span><span>${o}</span></div>`).join("")+
 `<div class="card" style="margin-top:15px"><b>Explanation</b><p class="muted">${q.explanation}</p></div>`;
 $("flagBtn").style.display="none";
 $("answeredCounter").textContent="Correct answer: "+ "ABCD"[q.answer];
 $("prevBtn").disabled=examIndex===0;
 $("nextBtn").style.display=examIndex===examQuestions.length-1?"none":"inline-block";
 $("submitBtn").style.display=examIndex===examQuestions.length-1?"inline-block":"none";
 $("submitBtn").textContent="Finish review";
 $("submitBtn").onclick=closeExam;
 $("prevBtn").onclick=()=>{examIndex--;renderReviewQuestion()};
 $("nextBtn").onclick=()=>{examIndex++;renderReviewQuestion()};
}
function leaveExam(){
 if(examRunning&&!confirm("Leave this exam? Your current attempt will not be submitted."))return;
 closeExam();
}
function closeExam(){
 clearInterval(timer);examRunning=false;
 $("exam").classList.remove("active");
 $("flagBtn").style.display="inline-block";
 $("submitBtn").textContent="Submit Test";$("submitBtn").onclick=confirmSubmit;
 $("prevBtn").onclick=examPrevious;$("nextBtn").onclick=examNext;
 if(document.fullscreenElement)document.exitFullscreen?.();
}
function toggleFullscreen(){
 if(!document.fullscreenElement)document.documentElement.requestFullscreen?.().catch(()=>{});
 else document.exitFullscreen?.();
}

/* Data and mistakes */
function renderMistakes(){
 const wrong=questions.filter(q=>answers[q.id]&&!answers[q.id].correct);
 $("mistakesList").innerHTML=wrong.length?wrong.map(q=>`
 <div class="list-item"><div><b>${q.topic}</b><p class="muted">${q.text.slice(0,90)}...</p></div>
 <button class="secondary" onclick="launchExam('${q.topic}',${q.id})">Review</button></div>`).join(""):'<div class="empty">No mistakes to review yet.</div>';
}
function renderData(){
 const s=stats();
 $("dataAnswered").textContent=s.total;$("dataCorrect").textContent=s.correct;
 $("dataWrong").textContent=s.wrong;$("dataAccuracy").textContent=s.total?s.accuracy+"%":"—";
 $("topicStats").innerHTML=topics.map(t=>{
  const qs=questions.filter(q=>q.topic===t),done=qs.filter(q=>answers[q.id]),correct=done.filter(q=>answers[q.id].correct).length;
  return `<div style="margin:20px 0"><b>${t}</b><span class="muted" style="float:right">${done.length}/${qs.length} answered</span><div class="progress"><span style="width:${done.length?correct/done.length*100:0}%"></span></div></div>`;
 }).join("");
}
init();
</script>
</body>
</html>
