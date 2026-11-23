
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify — SAT Platform</title>
<style>
:root{
 --bg:#f5f7fb;--panel:#fff;--text:#172033;--muted:#788398;
 --line:#e8edf4;--primary:#6256e8;--soft:#f0efff;
 --green:#159b72;--red:#df5968;--shadow:0 8px 28px #202b4510;
}
body.dark{--bg:#111522;--panel:#1a2030;--text:#eef1fa;--muted:#9aa5bb;--line:#2b3448;--primary:#9288ff;--soft:#292644;--shadow:0 8px 28px #0003}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Arial,sans-serif}
button,input,select{font:inherit}
button{cursor:pointer}
.app{display:flex;min-height:100vh}
.sidebar{width:250px;background:var(--panel);border-right:1px solid var(--line);padding:23px 15px;display:flex;flex-direction:column;position:fixed;top:0;bottom:0;left:0;z-index:10;overflow-y:auto}
.logo{display:flex;align-items:center;gap:10px;padding:0 12px 27px;font-size:23px;font-weight:800}
.logo-mark{width:35px;height:35px;border-radius:11px;background:linear-gradient(135deg,var(--primary),#a69dff);display:grid;place-items:center;color:white}
.nav-label{font-size:10px;color:var(--muted);font-weight:800;letter-spacing:1.5px;padding:14px 12px 8px}
.nav-btn{border:0;background:transparent;color:var(--muted);padding:12px;border-radius:10px;text-align:left;width:100%;display:flex;gap:12px;align-items:center;font-size:13px;font-weight:650;margin:2px 0}
.nav-btn:hover,.nav-btn.active{background:var(--soft);color:var(--primary)}
.nav-icon{width:18px;text-align:center}
.sidebar-bottom{margin-top:auto;border-top:1px solid var(--line);padding-top:13px}
.profile-mini{display:flex;align-items:center;gap:10px;padding:12px;overflow:hidden}
.avatar{width:35px;height:35px;border-radius:50%;background:var(--soft);color:var(--primary);display:grid;place-items:center;font-weight:800;flex-shrink:0}
.profile-mini small{display:block;color:var(--muted);margin-top:3px}
.main{margin-left:250px;width:calc(100% - 250px);padding:30px 38px 60px;min-width:0}
.topbar{display:flex;align-items:center;justify-content:space-between;margin-bottom:28px;gap:15px}
.eyebrow{color:var(--muted);font-size:12px;margin-bottom:7px}
h1{font-size:27px;margin:0;font-weight:800}
h2{font-size:19px;margin:0 0 13px}
h3{font-size:15px;margin:0 0 8px}
.top-actions{display:flex;gap:9px}
.icon-btn,.secondary{border:1px solid var(--line);background:var(--panel);color:var(--text);border-radius:10px;padding:10px 13px}
.primary{background:var(--primary);color:white;border:0;border-radius:10px;padding:11px 17px;font-weight:700}
.primary:hover{filter:brightness(1.08)}
.card{background:var(--panel);border:1px solid var(--line);border-radius:15px;padding:20px;box-shadow:var(--shadow)}
.grid{display:grid;gap:16px}
.stats{grid-template-columns:repeat(4,minmax(0,1fr));margin-bottom:20px}
.stat-label{color:var(--muted);font-size:12px}
.stat-value{font-size:27px;font-weight:800;margin:9px 0 5px}
.stat-note,.muted{color:var(--muted);font-size:12px;line-height:1.6}
.progress{height:8px;border-radius:20px;background:var(--line);overflow:hidden;margin:12px 0}
.progress span{display:block;height:100%;background:var(--primary);border-radius:20px}
.dashboard-grid{grid-template-columns:1.4fr 1fr}
.course-grid{grid-template-columns:repeat(2,minmax(0,1fr))}
.course{display:flex;gap:14px;align-items:center}
.course-icon{width:43px;height:43px;border-radius:13px;background:var(--soft);display:grid;place-items:center;font-size:19px}
.course p{color:var(--muted);font-size:12px;margin:5px 0 0}
.course .secondary{margin-left:auto;white-space:nowrap}
.topic-list{display:grid;gap:9px}
.topic-row{display:flex;justify-content:space-between;align-items:center;padding:13px;border:1px solid var(--line);border-radius:11px;gap:10px}
.topic-row small{display:block;color:var(--muted);margin-top:4px}
.tag{font-size:10px;background:var(--soft);color:var(--primary);padding:5px 8px;border-radius:20px;font-weight:750}
.page{display:none}.page.active{display:block}
.welcome{background:linear-gradient(115deg,#5147ce,#8277f5);color:white;border:0;padding:27px;margin-bottom:20px}
.welcome p{opacity:.85;font-size:13px;line-height:1.6;max-width:540px}
.welcome .primary{background:white;color:#5147ce}
.section-heading{display:flex;justify-content:space-between;align-items:center;margin:25px 0 14px}
.section-heading h2{margin:0}
.filters{display:flex;gap:10px;flex-wrap:wrap;margin:18px 0}
.filters select,.search{background:var(--panel);color:var(--text);border:1px solid var(--line);border-radius:9px;padding:11px 12px}
.search{min-width:210px;flex:1}
.question-layout{display:grid;grid-template-columns:minmax(0,1fr) 250px;gap:17px}
.question-card{min-height:400px}
.q-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:22px;gap:10px}
.q-meta{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.question-text{font-size:17px;line-height:1.7;margin:18px 0 22px;white-space:pre-line}
.options{display:grid;gap:10px}
.option{display:flex;align-items:flex-start;gap:12px;padding:13px;border:1px solid var(--line);border-radius:10px;cursor:pointer;line-height:1.5}
.option:hover{border-color:var(--primary)}
.option.selected{border-color:var(--primary);background:var(--soft)}
.option.correct{border-color:var(--green);background:#159b7210}
.option.wrong{border-color:var(--red);background:#df596810}
.option-letter{width:25px;height:25px;border-radius:7px;background:var(--bg);display:grid;place-items:center;font-size:12px;font-weight:800;flex-shrink:0}
.feedback{display:none;margin-top:17px;padding:14px;border-radius:10px;line-height:1.6;font-size:13px}
.feedback.show{display:block}.feedback.good{background:#159b7212;color:var(--green)}.feedback.bad{background:#df596812;color:var(--red)}
.q-actions{display:flex;justify-content:space-between;gap:10px;margin-top:22px;flex-wrap:wrap}
.side-info{display:grid;gap:12px;align-content:start}
.question-nav{display:grid;grid-template-columns:repeat(5,1fr);gap:7px;margin-top:12px}
.qnum{border:1px solid var(--line);background:var(--panel);color:var(--text);border-radius:7px;padding:8px 0;font-size:11px}
.qnum.current{background:var(--soft);border-color:var(--primary);color:var(--primary)}
.qnum.done{background:#159b7215;border-color:#159b7255}
.empty{text-align:center;padding:45px 20px;color:var(--muted)}
.table{width:100%;border-collapse:collapse;font-size:13px}
.table th,.table td{text-align:left;padding:13px;border-bottom:1px solid var(--line)}
.table th{color:var(--muted);font-size:11px}
.modal-bg{position:fixed;inset:0;background:#080d1acc;display:none;place-items:center;z-index:30;padding:20px}
.modal-bg.show{display:grid}
.modal{background:var(--panel);padding:27px;border-radius:16px;width:min(460px,100%);box-shadow:var(--shadow)}
.modal input,.modal select{width:100%;padding:12px;border:1px solid var(--line);background:var(--bg);color:var(--text);border-radius:9px;margin:7px 0 15px}
.modal label{font-size:12px;color:var(--muted);font-weight:700}
.login-screen{min-height:100vh;display:grid;place-items:center;padding:20px}
.login-box{width:min(430px,100%);background:var(--panel);padding:35px;border:1px solid var(--line);border-radius:18px;box-shadow:var(--shadow)}
.login-box input{width:100%;padding:13px;border:1px solid var(--line);background:var(--bg);color:var(--text);border-radius:9px;margin:8px 0 15px}
.login-box label{font-size:12px;color:var(--muted);font-weight:700}
.login-box .primary{width:100%;padding:13px}
.small-note{font-size:11px;color:var(--muted);line-height:1.6;margin-top:15px}
.mobile-menu{display:none}

/* FULL SCREEN EXAM */
.exam-screen{display:none;position:fixed;inset:0;z-index:100;background:var(--bg);color:var(--text);overflow:auto}
.exam-screen.active{display:flex;flex-direction:column}
.exam-header{height:72px;flex-shrink:0;background:var(--panel);border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;padding:0 4%;gap:15px}
.exam-brand{font-weight:800;font-size:21px;display:flex;align-items:center;gap:10px}
.exam-header-right{display:flex;align-items:center;gap:13px}
.exam-clock{font-size:21px;font-weight:800;font-variant-numeric:tabular-nums;min-width:80px;text-align:center}
.exam-clock.warning{color:var(--red)}
.exam-content{width:min(1050px,92%);margin:0 auto;padding:35px 0 120px;flex:1}
.exam-progress-line{height:5px;background:var(--line);border-radius:10px;margin:15px 0 27px;overflow:hidden}
.exam-progress-line span{height:100%;display:block;background:var(--primary);transition:.2s}
.exam-question-head{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}
.exam-question-number{font-size:13px;color:var(--muted);font-weight:700}
.exam-question{font-size:20px;line-height:1.75;white-space:pre-line;margin:30px 0}
.exam-options{max-width:850px;display:grid;gap:13px}
.exam-options .option{padding:17px;font-size:16px;border-radius:12px}
.exam-options .option-letter{width:30px;height:30px}
.exam-footer{position:fixed;bottom:0;left:0;right:0;background:var(--panel);border-top:1px solid var(--line);padding:15px 4%;display:flex;justify-content:space-between;align-items:center;gap:12px;z-index:2}
.exam-footer-left,.exam-footer-right{display:flex;align-items:center;gap:10px}
.exam-nav-panel{display:none;background:var(--panel);border:1px solid var(--line);border-radius:12px;padding:17px;margin-top:22px}
.exam-nav-panel.show{display:block}
.exam-nav-grid{display:grid;grid-template-columns:repeat(10,1fr);gap:8px;margin-top:12px}
.exam-nav-grid button{padding:11px 5px;border:1px solid var(--line);background:var(--bg);color:var(--text);border-radius:8px}
.exam-nav-grid button.current{border:2px solid var(--primary);color:var(--primary)}
.exam-nav-grid button.answered{background:#159b7218;border-color:#159b7277}
.exam-nav-grid button.flagged:after{content:" ⚑";color:var(--red)}
.exam-instructions{max-width:680px;margin:55px auto;background:var(--panel);border:1px solid var(--line);border-radius:18px;padding:35px;box-shadow:var(--shadow)}
.mode-choice{display:grid;grid-template-columns:1fr 1fr;gap:13px;margin:22px 0}
.mode-card{border:2px solid var(--line);border-radius:12px;padding:18px;cursor:pointer}
.mode-card.active{border-color:var(--primary);background:var(--soft)}
.mode-card b{display:block;margin-bottom:7px}
.mode-card p{font-size:12px;color:var(--muted);line-height:1.5;margin:0}
.exam-instructions select{padding:12px;border:1px solid var(--line);border-radius:9px;background:var(--bg);color:var(--text);width:100%;margin:8px 0 18px}
.exam-result{text-align:center;padding:35px 10px}
.exam-result .score{font-size:55px;font-weight:850;margin:15px 0}
.exam-result .result-detail{display:flex;justify-content:center;gap:30px;flex-wrap:wrap;margin:25px 0}
.exam-result .result-detail b{display:block;font-size:22px;margin-bottom:5px}
@media(max-width:1000px){.stats{grid-template-columns:repeat(2,1fr)}.dashboard-grid{grid-template-columns:1fr}.question-layout{grid-template-columns:1fr}.side-info{grid-template-columns:repeat(2,1fr)}}
@media(max-width:700px){
 .sidebar{transform:translateX(-100%);transition:.2s}.sidebar.open{transform:translateX(0)}
 .main{margin-left:0;width:100%;padding:20px 14px 40px}
 .mobile-menu{display:inline-block}.course-grid{grid-template-columns:1fr}
 .side-info{grid-template-columns:1fr}.exam-header{padding:0 14px;height:62px}
 .exam-content{padding:23px 0 110px;width:92%}
 .exam-question{font-size:17px;margin:22px 0}
 .exam-footer{padding:12px}.exam-footer .secondary{padding:9px}
 .exam-footer-left .muted{display:none}.exam-nav-grid{grid-template-columns:repeat(5,1fr)}
 .exam-instructions{margin:20px auto;padding:22px}.mode-choice{grid-template-columns:1fr}
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
  <p class="small-note">Prototype login: email is stored only in this browser. Real authentication requires a backend.</p>
 </div>
</div>

<div class="app" id="app" style="display:none">
 <aside class="sidebar" id="sidebar">
  <div class="logo"><span class="logo-mark">P</span> Prepify</div>
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
   <div class="profile-mini"><div class="avatar" id="avatar">P</div><div style="min-width:0"><b id="profileEmail" style="font-size:12px;overflow-wrap:anywhere">Student</b><small>Prepify student</small></div></div>
  </div>
 </aside>

 <main class="main">
  <div class="topbar">
   <div style="display:flex;align-items:center;gap:12px">
    <button class="icon-btn mobile-menu" id="menuBtn">☰</button>
    <div><div class="eyebrow">YOUR STUDY SPACE</div><h1 id="pageTitle">Dashboard</h1></div>
   </div>
   <div class="top-actions"><button class="icon-btn" id="fontDown">A−</button><button class="icon-btn" id="fontUp">A+</button><button class="icon-btn" id="themeTop">◐</button></div>
  </div>

  <section class="page active" id="page-dashboard">
   <div class="card welcome">
    <div class="eyebrow" style="color:#e2dfff">YOUR PERSONAL SAT WORKSPACE</div>
    <h2 style="font-size:25px;margin:8px 0">Make every practice count.</h2>
    <p>Build your skills, focus on your weak areas, and track your SAT preparation in one place.</p>
    <button class="primary" onclick="showPage('bank')">Start practicing →</button>
   </div>
   <div class="grid stats">
    <div class="card"><div class="stat-label">Questions answered</div><div class="stat-value" id="statAnswered">0</div></div>
    <div class="card"><div class="stat-label">Accuracy</div><div class="stat-value" id="statAccuracy">—</div></div>
    <div class="card"><div class="stat-label">Saved questions</div><div class="stat-value" id="statSaved">0</div></div>
    <div class="card"><div class="stat-label">Mistakes to review</div><div class="stat-value" id="statMistakes">0</div></div>
   </div>
   <div class="grid dashboard-grid">
    <div class="card">
     <h2>Daily study goals</h2>
     <div style="display:flex;justify-content:space-between;font-size:13px"><b>Math</b><span class="muted" id="mathGoalText">0 / 10</span></div>
     <div class="progress"><span id="mathGoalBar" style="width:0%"></span></div>
     <div style="display:flex;justify-content:space-between;font-size:13px;margin-top:20px"><b>Reading & Writing</b><span class="muted" id="rwGoalText">0 / 10</span></div>
     <div class="progress"><span id="rwGoalBar" style="width:0%"></span></div>
     <button class="secondary" onclick="openSettings()">Edit study goals</button>
    </div>
    <div class="card">
     <h2>Continue learning</h2>
     <div class="topic-list">
      <div class="topic-row"><div><b>Writing Question Bank</b><small>4 skills · Sample questions</small></div><button class="secondary" onclick="showPage('bank')">Open</button></div>
      <div class="topic-row"><div><b>Practice Test</b><small>Timed or untimed full-screen practice</small></div><button class="secondary" onclick="showPage('practice')">Start</button></div>
      <div class="topic-row"><div><b>My Mistakes</b><small>Review incorrect answers</small></div><button class="secondary" onclick="showPage('mistakes')">Review</button></div>
     </div>
    </div>
   </div>
   <div class="section-heading"><h2>Reading & Writing skills</h2><button class="secondary" onclick="showPage('bank')">View all</button></div>
   <div class="grid course-grid" id="dashboardTopics"></div>
  </section>

  <section class="page" id="page-bank">
   <div class="card">
    <div class="section-heading" style="margin-top:0"><div><h2>Question Bank</h2><p class="muted">Practice by skill and focus on your weak areas.</p></div><span class="tag">READING & WRITING</span></div>
    <div class="filters">
     <input class="search" id="searchInput" placeholder="Search questions or skills...">
     <select id="topicFilter"><option value="All">All topics</option><option>Boundaries</option><option>Form, Structure & Sense</option><option>Transitions</option><option>Rhetorical Synthesis</option></select>
     <select id="statusFilter"><option value="All">All questions</option><option value="Unanswered">Not answered</option><option value="Correct">Correct</option><option value="Wrong">Incorrect</option><option value="Saved">Bookmarked</option></select>
    </div>
    <div class="question-layout">
     <div class="card question-card" style="box-shadow:none" id="questionArea"><div class="empty">Choose a topic or question to begin.</div></div>
     <div class="side-info">
      <div class="card"><h3>Question progress</h3><div class="stat-value" id="bankProgress">0/0</div><div class="progress"><span id="bankProgressBar"></span></div><p class="muted">Questions you have answered.</p></div>
      <div class="card"><h3>Question navigator</h3><div class="question-nav" id="questionNav"></div></div>
      <div class="card"><h3>Study tip</h3><p class="muted">Read carefully. After checking your answer, review the explanation.</p></div>
     </div>
    </div>
   </div>
  </section>

  <section class="page" id="page-practice">
   <div class="card">
    <h2>Practice Test</h2>
    <p class="muted">Take a test in a dedicated full-screen exam environment, just like a real testing interface.</p>
    <div class="grid stats" style="grid-template-columns:repeat(3,1fr)">
     <div class="card"><div class="stat-label">Sample questions</div><div class="stat-value">5</div></div>
     <div class="card"><div class="stat-label">Topics</div><div class="stat-value">4</div></div>
     <div class="card"><div class="stat-label">Exam display</div><div class="stat-value" style="font-size:20px">Full screen</div></div>
    </div>
    <button class="primary" onclick="openExamSetup()">Set up your exam →</button>
   </div>
  </section>

  <section class="page" id="page-mistakes">
   <div class="card"><h2>My Mistakes</h2><p class="muted">Questions you answered incorrectly.</p><div id="mistakeList"></div></div>
  </section>

  <section class="page" id="page-data">
   <div class="grid stats">
    <div class="card"><div class="stat-label">Total answered</div><div class="stat-value" id="dataAnswered">0</div></div>
    <div class="card"><div class="stat-label">Correct</div><div class="stat-value" id="dataCorrect">0</div></div>
    <div class="card"><div class="stat-label">Incorrect</div><div class="stat-value" id="dataWrong">0</div></div>
    <div class="card"><div class="stat-label">Accuracy</div><div class="stat-value" id="dataAccuracy">—</div></div>
   </div>
   <div class="card"><h2>Performance by topic</h2><div id="topicPerformance"></div></div>
  </section>

  <section class="page" id="page-materials">
   <div class="card"><h2>Study Materials</h2><div class="topic-list">
    <div class="topic-row"><div><b>College Board — SAT Suite</b><small>Official SAT information.</small></div><a href="https://satsuite.collegeboard.org/" target="_blank">Open ↗</a></div>
    <div class="topic-row"><div><b>Bluebook</b><small>Official digital testing application.</small></div><a href="https://bluebook.collegeboard.org/" target="_blank">Open ↗</a></div>
    <div class="topic-row"><div><b>Khan Academy</b><small>Free SAT lessons and practice.</small></div><a href="https://www.khanacademy.org/test-prep/sat" target="_blank">Open ↗</a></div>
    <div class="topic-row"><div><b>College Board Question Bank</b><small>Official practice questions.</small></div><a href="https://satsuitequestionbank.collegeboard.org/" target="_blank">Open ↗</a></div>
   </div></div>
  </section>
 </main>
</div>

<!-- FULL SCREEN EXAM WINDOW -->
<div class="exam-screen" id="examScreen">
 <header class="exam-header">
  <div class="exam-brand"><span class="logo-mark">P</span> Prepify <span class="muted" style="font-weight:400;font-size:12px">| Practice Exam</span></div>
  <div class="exam-header-right">
   <span class="muted" id="examModeLabel">TIMED</span>
   <div class="exam-clock" id="examClock">32:00</div>
   <button class="icon-btn" onclick="toggleExamFullscreen()" title="Toggle fullscreen">⛶</button>
   <button class="icon-btn" onclick="exitExam()" title="Exit exam">✕</button>
  </div>
 </header>
 <div class="exam-content">
  <div id="examSetup">
   <div class="exam-instructions">
    <div class="eyebrow">PREPIFY PRACTICE ENVIRONMENT</div>
    <h1 style="font-size:29px;margin-bottom:12px">Ready for your exam?</h1>
    <p class="muted">Before you begin, choose how you want to practice. Your questions will appear only after you press Start Exam.</p>
    <h3 style="margin-top:25px">Choose your mode</h3>
    <div class="mode-choice">
     <div class="mode-card active" id="timedChoice" onclick="chooseMode('timed')">
      <b>◷ Timed Mode</b>
      <p>Complete the test with a countdown timer. Practice managing your time under exam conditions.</p>
     </div>
     <div class="mode-card" id="untimedChoice" onclick="chooseMode('untimed')">
      <b>∞ Untimed Mode</b>
      <p>Take as much time as you need. Focus on accuracy and understanding.</p>
     </div>
    </div>
    <div id="durationWrap">
     <label for="durationSelect">Time limit</label>
     <select id="durationSelect">
      <option value="10">10 minutes — Quick practice</option>
      <option value="20">20 minutes — Extended practice</option>
      <option value="32" selected>32 minutes — SAT-style module timing</option>
     </select>
    </div>
    <div class="topic-row" style="margin:18px 0">
     <div><b>Question count</b><small>5 questions selected from your Writing practice bank</small></div><span class="tag">5 QUESTIONS</span>
    </div>
    <div class="topic-row" style="margin-bottom:20px">
     <div><b>Exam interface</b><small>Full-screen layout · Question navigator · Mark for review</small></div><span class="tag">EXAM MODE</span>
    </div>
    <button class="primary" style="width:100%;padding:15px" onclick="startExam()">Start Exam →</button>
    <p class="muted" style="text-align:center;margin-top:12px">Starting the exam will open the full-screen testing interface.</p>
   </div>
  </div>
  <div id="examQuestionArea" style="display:none">
   <div class="exam-question-head">
    <span class="exam-question-number" id="examQuestionNumber">QUESTION 1 OF 5</span>
    <button class="secondary" id="flagButton" onclick="toggleFlag()">⚑ Mark for review</button>
   </div>
   <div class="exam-progress-line"><span id="examProgressBar" style="width:20%"></span></div>
   <div class="muted" id="examTopic"></div>
   <div class="exam-question" id="examQuestionText"></div>
   <div class="exam-options" id="examOptions"></div>
   <div class="exam-nav-panel" id="examNavPanel">
    <b>Question navigator</b><p class="muted">Select a question to move directly to it.</p>
    <div class="exam-nav-grid" id="examNavGrid"></div>
   </div>
  </div>
  <div id="examResult" style="display:none"></div>
 </div>
 <footer class="exam-footer" id="examFooter" style="display:none">
  <div class="exam-footer-left">
   <button class="secondary" onclick="toggleExamNav()">☷ <span class="muted">Questions</span></button>
   <span class="muted" id="examAnsweredCount">0 of 5 answered</span>
  </div>
  <div class="exam-footer-right">
   <button class="secondary" id="examPrev" onclick="examPrevious()">← Back</button>
   <button class="primary" id="examNext" onclick="examNext()">Next →</button>
   <button class="primary" id="examSubmit" onclick="confirmSubmit()" style="display:none">Submit Test</button>
  </div>
 </footer>
</div>

<div class="modal-bg" id="setupModal">
 <div class="modal">
  <div class="logo" style="padding:0 0 15px"><span class="logo-mark">P</span> Prepify</div>
  <h2>Set up your study plan</h2>
  <p class="muted">Choose your targets and daily goals.</p>
  <form id="setupForm">
   <label>Target Math score (200–800)</label><input type="number" id="targetMath" min="200" max="800" value="700" required>
   <label>Target Reading & Writing score (200–800)</label><input type="number" id="targetRW" min="200" max="800" value="700" required>
   <label>Daily Math lessons</label><input type="number" id="dailyMath" min="1" max="50" value="10" required>
   <label>Daily Reading & Writing lessons</label><input type="number" id="dailyRW" min="1" max="50" value="10" required>
   <button class="primary" type="submit" style="width:100%">Save my study plan</button>
  </form>
 </div>
</div>

<script>
const topics=["Boundaries","Form, Structure & Sense","Transitions","Rhetorical Synthesis"];
const questions=[
{id:1,topic:"Boundaries",difficulty:"Medium",text:"The research team collected data from several coastal regions ____ the results revealed a clear pattern in water temperature.",options:["regions, and the","regions; the","regions the","regions, the"],answer:1,explanation:"The sentence contains two independent clauses. A semicolon can correctly join two closely related independent clauses."},
{id:2,topic:"Boundaries",difficulty:"Medium",text:"Although the experiment was initially considered unsuccessful ____ the researchers later discovered an important result.",options:["unsuccessful,","unsuccessful;","unsuccessful","unsuccessful:"],answer:0,explanation:"An introductory dependent clause beginning with “Although” is followed by a comma before the main clause."},
{id:3,topic:"Form, Structure & Sense",difficulty:"Medium",text:"The collection of rare plants ____ carefully maintained by the university's biology department.",options:["are","were","is","have been"],answer:2,explanation:"The subject is “collection,” which is singular. The verb must therefore be singular: “is.”"},
{id:4,topic:"Form, Structure & Sense",difficulty:"Hard",text:"By the time the final report was published, the scientists ____ the data for nearly three years.",options:["analyze","had been analyzing","will analyze","are analyzing"],answer:1,explanation:"The past perfect progressive describes an activity that continued before another past event."},
{id:5,topic:"Transitions",difficulty:"Medium",text:"The first design was inexpensive to produce. ____, it required frequent repairs, making it costly over time.",options:["For example","Nevertheless","Similarly","In addition"],answer:1,explanation:"“Nevertheless” signals a contrast between the low initial cost and the later repair expenses."},
{id:6,topic:"Transitions",difficulty:"Hard",text:"Several studies have examined the effects of urban green spaces on air quality. ____, recent research has also explored their influence on residents' mental well-being.",options:["In contrast","As a result","Furthermore","Instead"],answer:2,explanation:"“Furthermore” adds another related point to the information already presented."},
{id:7,topic:"Rhetorical Synthesis",difficulty:"Medium",text:"A student is writing about a museum exhibition. The student wants to emphasize that the exhibition includes works from different historical periods.\n\nNotes:\n• The exhibition opened in 2024.\n• It contains 60 paintings.\n• The paintings were created between 1600 and 1950.\n• The exhibition is located in the city art museum.\n\nWhich choice most effectively uses the notes to achieve the student's goal?",options:["The city art museum opened an exhibition in 2024.","The exhibition features 60 paintings created across a period spanning from 1600 to 1950.","The museum is located in the city center.","Sixty paintings are included in the exhibition."],answer:1,explanation:"This choice directly emphasizes the range of historical periods represented by the paintings."},
{id:8,topic:"Rhetorical Synthesis",difficulty:"Hard",text:"A student is writing about a scientific discovery. The student wants to compare the two methods used in the study.\n\nNotes:\n• Method A took 12 hours to complete.\n• Method B took 4 hours to complete.\n• Both methods produced results with similar accuracy.\n\nWhich choice best achieves the student's goal?",options:["The study used two methods to collect scientific data.","Method A and Method B both produced accurate results.","Although Method A took longer, both methods achieved similar levels of accuracy.","Method B was used in a scientific study."],answer:2,explanation:"This choice compares the time required by each method while highlighting their similar accuracy."}
];

let user=localStorage.getItem("prepify_email")||"";
let profile=JSON.parse(localStorage.getItem("prepify_profile")||"null");
let answers=JSON.parse(localStorage.getItem("prepify_answers")||"{}");
let saved=JSON.parse(localStorage.getItem("prepify_saved")||"[]");
let currentIndex=0,selected=null,fontSize=100;
let examMode="timed",examQuestions=[],examIndex=0,examAnswers={},examFlags=[];
let examRemaining=0,examInterval=null,examStarted=false;
const $=id=>document.getElementById(id);

function init(){
 if(!user){$("loginScreen").style.display="grid";$("app").style.display="none";return}
 $("loginScreen").style.display="none";$("app").style.display="flex";
 $("profileEmail").textContent=user;$("avatar").textContent=user[0].toUpperCase();
 if(!profile){$("setupModal").classList.add("show")}else{$("setupModal").classList.remove("show");renderDashboard()}
}
$("loginForm").onsubmit=e=>{
 e.preventDefault();user=$("emailInput").value.trim().toLowerCase();
 localStorage.setItem("prepify_email",user);profile=JSON.parse(localStorage.getItem("prepify_profile")||"null");init();
};
$("setupForm").onsubmit=e=>{
 e.preventDefault();profile={targetMath:+$("targetMath").value,targetRW:+$("targetRW").value,dailyMath:+$("dailyMath").value,dailyRW:+$("dailyRW").value};
 localStorage.setItem("prepify_profile",JSON.stringify(profile));$("setupModal").classList.remove("show");renderDashboard();
};
function openSettings(){
 $("targetMath").value=profile.targetMath;$("targetRW").value=profile.targetRW;
 $("dailyMath").value=profile.dailyMath;$("dailyRW").value=profile.dailyRW;$("setupModal").classList.add("show");
}
$("logoutBtn").onclick=()=>{localStorage.removeItem("prepify_email");user="";profile=null;init()};
$("themeBtn").onclick=$("themeTop").onclick=()=>{
 document.body.classList.toggle("dark");localStorage.setItem("prepify_theme",document.body.classList.contains("dark")?"dark":"light");
};
if(localStorage.getItem("prepify_theme")==="dark")document.body.classList.add("dark");
$("fontDown").onclick=()=>{fontSize=Math.max(85,fontSize-5);$("app").style.fontSize=fontSize+"%"};
$("fontUp").onclick=()=>{fontSize=Math.min(120,fontSize+5);$("app").style.fontSize=fontSize+"%"};
$("menuBtn").onclick=()=>$("sidebar").classList.toggle("open");

const pageNames={dashboard:"Dashboard",bank:"Question Bank",practice:"Practice Test",mistakes:"My Mistakes",data:"My Data",materials:"Study Materials"};
function showPage(name){
 document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
 $("page-"+name).classList.add("active");
 document.querySelectorAll("[data-page]").forEach(b=>b.classList.remove("active"));
 const btn=document.querySelector('[data-page="'+name+'"]');if(btn)btn.classList.add("active");
 $("pageTitle").textContent=pageNames[name];$("sidebar").classList.remove("open");
 if(name==="dashboard")renderDashboard();if(name==="bank")renderBank();if(name==="mistakes")renderMistakes();if(name==="data")renderData();
}
document.querySelectorAll("[data-page]").forEach(b=>b.onclick=()=>showPage(b.dataset.page));
document.querySelectorAll(".topic-link").forEach(b=>b.onclick=()=>{$("topicFilter").value=b.dataset.topic;showPage("bank");renderBank()});

function getStats(){
 const vals=Object.values(answers),correct=vals.filter(x=>x.correct).length;
 return {total:vals.length,correct,wrong:vals.length-correct,accuracy:vals.length?Math.round(correct/vals.length*100):0};
}
function renderDashboard(){
 const s=getStats();
 $("statAnswered").textContent=s.total;$("statAccuracy").textContent=s.total?s.accuracy+"%":"—";
 $("statSaved").textContent=saved.length;$("statMistakes").textContent=s.wrong;
 const rwDone=s.total;
 $("mathGoalText").textContent="0 / "+profile.dailyMath+" lessons";
 $("rwGoalText").textContent=rwDone+" / "+profile.dailyRW+" lessons";
 $("mathGoalBar").style.width="0%";$("rwGoalBar").style.width=Math.min(100,rwDone/profile.dailyRW*100)+"%";
 $("dashboardTopics").innerHTML=topics.map((t,i)=>`<div class="card course"><div class="course-icon">${["Aa","✎","⇄","✦"][i]}</div><div style="flex:1"><b>${t}</b><p>${questions.filter(q=>q.topic===t).length} sample questions</p></div><button class="secondary" onclick="chooseTopic('${t}')">Practice</button></div>`).join("");
}
function chooseTopic(t){$("topicFilter").value=t;showPage("bank");renderBank()}
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
 $("questionNav").innerHTML=list.map((q,i)=>`<button class="qnum ${questions[currentIndex]?.id===q.id?"current":""} ${answers[q.id]?"done":""}" onclick="openQuestion(${q.id})">${i+1}</button>`).join("");
 if(!list.length){$("questionArea").innerHTML='<div class="empty">No questions match these filters.</div>';return}
 if(!list.some(q=>q.id===questions[currentIndex]?.id))currentIndex=questions.indexOf(list[0]);
 renderQuestion(questions[currentIndex]);
}
function openQuestion(id){currentIndex=questions.findIndex(q=>q.id===id);renderBank()}
function renderQuestion(q){
 selected=null;const old=answers[q.id];
 $("questionArea").innerHTML=`
 <div class="q-top"><div class="q-meta"><span class="tag">${q.topic}</span><span class="muted">${q.difficulty}</span></div><button class="icon-btn" onclick="toggleSave(${q.id})">${saved.includes(q.id)?"★ Saved":"☆ Save"}</button></div>
 <div class="muted">QUESTION ${questions.indexOf(q)+1} OF ${questions.length}</div>
 <div class="question-text">${q.text}</div>
 <div class="options">${q.options.map((o,i)=>`<div class="option ${old&&i===q.answer?"correct":""} ${old&&old.choice===i&&!old.correct?"wrong":""}" onclick="selectOption(${i})" data-option="${i}"><span class="option-letter">${"ABCD"[i]}</span><span>${o}</span></div>`).join("")}</div>
 <div id="feedback" class="feedback ${old?"show "+(old.correct?"good":"bad"):""}">${old?(old.correct?"Correct! ":"Not quite. ")+"<b>Answer: "+ "ABCD"[q.answer]+"</b><br>"+q.explanation:""}</div>
 <div class="q-actions"><button class="secondary" onclick="previousQuestion()">← Previous</button><div style="display:flex;gap:8px"><button class="secondary" onclick="checkAnswer(${q.id})">Check answer</button><button class="primary" onclick="nextQuestion()">Next →</button></div></div>`;
}
function selectOption(i){selected=i;document.querySelectorAll("#questionArea .option").forEach(o=>o.classList.toggle("selected",+o.dataset.option===i))}
function checkAnswer(id){
 if(selected===null){alert("Please select an answer first.");return}
 const q=questions.find(x=>x.id===id);answers[id]={choice:selected,correct:selected===q.answer};
 persist();renderQuestion(q);renderDashboard();
}
function toggleSave(id){saved=saved.includes(id)?saved.filter(x=>x!==id):[...saved,id];persist();renderQuestion(questions.find(q=>q.id===id));renderDashboard()}
function nextQuestion(){const l=filteredQuestions();if(!l.length)return;let p=l.findIndex(q=>q.id===questions[currentIndex]?.id);currentIndex=questions.indexOf(l[(p+1)%l.length]);renderBank()}
function previousQuestion(){const l=filteredQuestions();if(!l.length)return;let p=l.findIndex(q=>q.id===questions[currentIndex]?.id);currentIndex=questions.indexOf(l[(p-1+l.length)%l.length]);renderBank()}
$("topicFilter").onchange=$("statusFilter").onchange=$("searchInput").oninput=()=>{currentIndex=0;renderBank()};
function renderMistakes(){
 const wrong=questions.filter(q=>answers[q.id]&&!answers[q.id].correct);
 $("mistakeList").innerHTML=wrong.length?wrong.map(q=>`<div class="topic-row"><div style="flex:1"><b>${q.topic}</b><small>${q.text.slice(0,100)}...</small></div><button class="secondary" onclick="showPage('bank');openQuestion(${q.id})">Review</button></div>`).join(""):'<div class="empty">No mistakes yet. Answer some questions to build your review list.</div>';
}
function renderData(){
 const s=getStats();$("dataAnswered").textContent=s.total;$("dataCorrect").textContent=s.correct;$("dataWrong").textContent=s.wrong;$("dataAccuracy").textContent=s.total?s.accuracy+"%":"—";
 $("topicPerformance").innerHTML=topics.map(t=>{
  const qs=questions.filter(q=>q.topic===t),done=qs.filter(q=>answers[q.id]),correct=done.filter(q=>answers[q.id].correct).length,pct=done.length?Math.round(correct/done.length*100):0;
  return `<div style="margin:17px 0"><div style="display:flex;justify-content:space-between;font-size:13px"><b>${t}</b><span class="muted">${done.length}/${qs.length} answered · ${done.length?pct+"% accuracy":"Not started"}</span></div><div class="progress"><span style="width:${pct}%"></span></div></div>`;
 }).join("");
}
function persist(){localStorage.setItem("prepify_answers",JSON.stringify(answers));localStorage.setItem("prepify_saved",JSON.stringify(saved))}

/* EXAM MODE */
function openExamSetup(){
 $("examScreen").classList.add("active");
 $("examSetup").style.display="block";$("examQuestionArea").style.display="none";
 $("examResult").style.display="none";$("examFooter").style.display="none";
 examStarted=false;
}
function chooseMode(mode){
 examMode=mode;
 $("timedChoice").classList.toggle("active",mode==="timed");
 $("untimedChoice").classList.toggle("active",mode==="untimed");
 $("durationWrap").style.display=mode==="timed"?"block":"none";
}
function startExam(){
 examQuestions=[...questions].sort(()=>Math.random()-.5).slice(0,5);
 examIndex=0;examAnswers={};examFlags=[];examStarted=true;
 examRemaining=Number($("durationSelect").value)*60;
 $("examSetup").style.display="none";$("examQuestionArea").style.display="block";
 $("examResult").style.display="none";$("examFooter").style.display="flex";
 $("examModeLabel").textContent=examMode==="timed"?"TIMED MODE":"UNTIMED MODE";
 if(examMode==="timed"){
  updateClock();clearInterval(examInterval);
  examInterval=setInterval(()=>{
   examRemaining--;updateClock();
   if(examRemaining<=0){clearInterval(examInterval);submitExam(true)}
  },1000);
 }else{$("examClock").textContent="∞";$("examClock").classList.remove("warning")}
 renderExamQuestion();
 document.documentElement.requestFullscreen?.().catch(()=>{});
}
function updateClock(){
 const m=Math.floor(examRemaining/60),s=examRemaining%60;
 $("examClock").textContent=String(m).padStart(2,"0")+":"+String(s).padStart(2,"0");
 $("examClock").classList.toggle("warning",examRemaining<=300);
}
function renderExamQuestion(){
 const q=examQuestions[examIndex];
 $("examQuestionNumber").textContent="QUESTION "+(examIndex+1)+" OF "+examQuestions.length;
 $("examProgressBar").style.width=((examIndex+1)/examQuestions.length*100)+"%";
 $("examTopic").textContent=q.topic+"  ·  "+q.difficulty;
 $("examQuestionText").textContent=q.text;
 $("examOptions").innerHTML=q.options.map((o,i)=>`
 <div class="option ${examAnswers[q.id]===i?"selected":""}" data-option="${i}" onclick="chooseExamAnswer(${i})">
 <span class="option-letter">${"ABCD"[i]}</span><span>${o}</span></div>`).join("");
 $("flagButton").textContent=examFlags.includes(q.id)?"⚑ Marked for review":"⚑ Mark for review";
 $("examPrev").disabled=examIndex===0;
 $("examNext").style.display=examIndex===examQuestions.length-1?"none":"inline-block";
 $("examSubmit").style.display=examIndex===examQuestions.length-1?"inline-block":"none";
 $("examAnsweredCount").textContent=Object.keys(examAnswers).length+" of "+examQuestions.length+" answered";
 renderExamNav();
}
function chooseExamAnswer(i){
 const q=examQuestions[examIndex];examAnswers[q.id]=i;renderExamQuestion();
}
function examPrevious(){if(examIndex>0){examIndex--;renderExamQuestion()}}
function examNext(){if(examIndex<examQuestions.length-1){examIndex++;renderExamQuestion()}}
function toggleFlag(){
 const id=examQuestions[examIndex].id;
 examFlags=examFlags.includes(id)?examFlags.filter(x=>x!==id):[...examFlags,id];
 renderExamQuestion();
}
function toggleExamNav(){$("examNavPanel").classList.toggle("show")}
function renderExamNav(){
 $("examNavGrid").innerHTML=examQuestions.map((q,i)=>`
 <button class="${i===examIndex?"current ":""}${examAnswers[q.id]!==undefined?"answered ":""}${examFlags.includes(q.id)?"flagged":""}" onclick="goExamQuestion(${i})">${i+1}</button>`).join("");
}
function goExamQuestion(i){examIndex=i;renderExamQuestion();$("examNavPanel").classList.remove("show")}
function confirmSubmit(){
 const unanswered=examQuestions.filter(q=>examAnswers[q.id]===undefined).length;
 const msg=unanswered?`You have ${unanswered} unanswered question(s). Submit anyway?`:"Are you sure you want to submit your test?";
 if(confirm(msg))submitExam(false);
}
function submitExam(timeUp){
 clearInterval(examInterval);
 examQuestions.forEach(q=>{
  if(examAnswers[q.id]!==undefined){
   answers[q.id]={choice:examAnswers[q.id],correct:examAnswers[q.id]===q.answer};
  }
 });
 persist();
 const correct=examQuestions.filter(q=>examAnswers[q.id]===q.answer).length;
 const attempted=Object.keys(examAnswers).length;
 const pct=Math.round(correct/examQuestions.length*100);
 $("examQuestionArea").style.display="none";$("examFooter").style.display="none";
 $("examResult").style.display="block";
 $("examResult").innerHTML=`
 <div class="exam-instructions exam-result">
  <div class="eyebrow">${timeUp?"TIME IS UP":"TEST SUBMITTED"}</div>
  <h1 style="font-size:30px">Practice completed!</h1>
  <div class="score">${correct}/${examQuestions.length}</div>
  <p class="muted">Correct answers · ${pct}% accuracy</p>
  <div class="result-detail">
   <div><b>${attempted}</b><span class="muted">Answered</span></div>
   <div><b>${examQuestions.length-attempted}</b><span class="muted">Unanswered</span></div>
   <div><b>${examQuestions.length-correct}</b><span class="muted">Incorrect</span></div>
  </div>
  <p class="muted">This is a result for this short Prepify sample test, not an official SAT score.</p>
  <button class="primary" onclick="reviewExam()">Review answers</button>
  <button class="secondary" style="margin-left:7px" onclick="closeExam()">Back to Prepify</button>
 </div>`;
 renderDashboard();
}
function reviewExam(){
 $("examResult").style.display="none";$("examQuestionArea").style.display="block";$("examFooter").style.display="flex";
 examIndex=0;renderExamReview();
}
function renderExamReview(){
 const q=examQuestions[examIndex];
 $("examQuestionNumber").textContent="REVIEW · QUESTION "+(examIndex+1)+" OF "+examQuestions.length;
 $("examProgressBar").style.width=((examIndex+1)/examQuestions.length*100)+"%";
 $("examTopic").textContent=q.topic+" · "+(examAnswers[q.id]===q.answer?"Correct":"Incorrect / Unanswered");
 $("examQuestionText").textContent=q.text;
 $("examOptions").innerHTML=q.options.map((o,i)=>`
 <div class="option ${i===q.answer?"correct":""} ${examAnswers[q.id]===i&&i!==q.answer?"wrong":""}">
 <span class="option-letter">${"ABCD"[i]}</span><span>${o}</span></div>`).join("");
 $("flagButton").style.display="none";
 $("examAnsweredCount").textContent="Answer: "+(examAnswers[q.id]===undefined?"Not answered":"ABCD"[q.answer]);
 $("examPrev").disabled=examIndex===0;
 $("examNext").style.display=examIndex===examQuestions.length-1?"none":"inline-block";
 $("examSubmit").style.display=examIndex===examQuestions.length-1?"inline-block":"none";
 $("examSubmit").textContent="Finish review";$("examSubmit").onclick=closeExam;
 $("examNext").onclick=()=>{examIndex++;renderExamReview()};
 $("examPrev").onclick=()=>{examIndex--;renderExamReview()};
 $("examOptions").insertAdjacentHTML("afterend",`<div class="feedback show good" style="margin-top:18px"><b>Explanation</b><br>${q.explanation}</div>`);
}
function toggleExamFullscreen(){
 if(!document.fullscreenElement)document.documentElement.requestFullscreen?.().catch(()=>{});
 else document.exitFullscreen?.();
}
function exitExam(){
 if(examStarted&&!$("examResult").style.display.includes("block")){
  if(!confirm("Exit the exam? Your current attempt will not be submitted."))return;
 }
 closeExam();
}
function closeExam(){
 clearInterval(examInterval);$("examScreen").classList.remove("active");
 $("flagButton").style.display="inline-block";$("examSubmit").textContent="Submit Test";
 $("examSubmit").onclick=confirmSubmit;
 if(document.fullscreenElement)document.exitFullscreen?.();
}
init();
</script>
</body>
</html>
