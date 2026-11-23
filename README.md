
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SATboost | SAT Preparation</title>
<style>
:root{
 --bg:#f5f6f8;
 --surface:#ffffff;
 --surface2:#f8f9fb;
 --text:#17202e;
 --muted:#778293;
 --border:#e4e8ee;
 --primary:#3157d5;
 --primary-light:#edf1ff;
 --green:#16845d;
 --green-bg:#eaf7f1;
 --red:#c74651;
 --red-bg:#fff0f0;
 --shadow:0 5px 24px rgba(25,40,70,.045);
}
body.dark{
 --bg:#10151e;
 --surface:#19212d;
 --surface2:#202a38;
 --text:#edf1f8;
 --muted:#a0adbf;
 --border:#303c4d;
 --primary:#8da5ff;
 --primary-light:#273453;
 --green:#55c99a;
 --green-bg:#19392f;
 --red:#ff8585;
 --red-bg:#40282d;
 --shadow:0 5px 24px rgba(0,0,0,.15);
}
*{box-sizing:border-box}
body{
 margin:0;background:var(--bg);color:var(--text);
 font-family:Arial,Helvetica,sans-serif;
}
button,input{font:inherit}
button{cursor:pointer}
button:disabled{opacity:.4;cursor:not-allowed}
.app{display:none;min-height:100vh}
.sidebar{
 width:255px;position:fixed;left:0;top:0;bottom:0;
 background:var(--surface);border-right:1px solid var(--border);
 display:flex;flex-direction:column;padding:22px 15px;
 z-index:30;overflow-y:auto;
}
.brand{
 display:flex;align-items:center;gap:11px;
 padding:2px 10px 34px;font-size:25px;font-weight:800;
 letter-spacing:-.8px;
}
.brand-icon{
 width:39px;height:39px;border-radius:10px;
 display:grid;place-items:center;background:#3157d5;
 color:white;font-size:23px;font-weight:800;
}
.nav-heading{
 font-size:10px;font-weight:800;letter-spacing:1.5px;
 color:var(--muted);padding:13px 12px 8px;
}
.nav-btn{
 border:0;background:transparent;color:var(--muted);
 text-align:left;width:100%;padding:13px 12px;
 border-radius:8px;font-size:13px;font-weight:650;
 margin:2px 0;display:flex;align-items:center;gap:11px;
}
.nav-btn:hover{background:var(--surface2);color:var(--text)}
.nav-btn.active{background:var(--primary-light);color:var(--primary)}
.nav-icon{width:17px;text-align:center;font-size:15px}
.sidebar-bottom{margin-top:auto;border-top:1px solid var(--border);padding-top:12px}
.profile{
 display:flex;align-items:center;gap:10px;padding:13px 9px;
 overflow-wrap:anywhere;
}
.avatar{
 width:34px;height:34px;border-radius:50%;background:var(--primary-light);
 color:var(--primary);display:grid;place-items:center;font-weight:800;flex-shrink:0;
}
.profile-email{font-size:11px;font-weight:700;overflow-wrap:anywhere}
.profile-role{font-size:11px;color:var(--muted);margin-top:4px}
.main{
 margin-left:255px;width:calc(100% - 255px);
 min-width:0;padding:30px 38px 65px;
}
.topbar{
 display:flex;justify-content:space-between;align-items:center;
 margin-bottom:30px;gap:15px;
}
.topbar-left{display:flex;align-items:center;gap:13px}
.eyebrow{
 font-size:10px;letter-spacing:1.3px;font-weight:800;
 color:var(--muted);margin-bottom:9px;
}
h1{font-size:29px;letter-spacing:-.7px;margin:0;font-weight:750}
h2{font-size:21px;margin:0 0 9px;letter-spacing:-.3px}
h3{font-size:16px;margin:0 0 8px}
p{line-height:1.65}
.muted{color:var(--muted);font-size:13px;line-height:1.65}
.page{display:none;width:100%;min-width:0}
.page.active{display:block}
.card{
 background:var(--surface);border:1px solid var(--border);
 border-radius:12px;box-shadow:var(--shadow);
}
.btn{
 border:1px solid var(--border);background:var(--surface);
 color:var(--text);border-radius:7px;padding:11px 16px;
 font-size:13px;font-weight:650;
}
.btn:hover{border-color:var(--primary)}
.btn-primary{background:var(--primary);border-color:var(--primary);color:white}
.btn-primary:hover{filter:brightness(1.08)}
.btn-light{background:var(--primary-light);border-color:transparent;color:var(--primary)}
.btn-row{display:flex;gap:9px;align-items:center;flex-wrap:wrap}
.tag{
 display:inline-flex;align-items:center;padding:6px 9px;
 border-radius:5px;background:var(--primary-light);
 color:var(--primary);font-size:10px;font-weight:800;
}
.stat-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin:20px 0}
.stat-card{padding:19px}
.stat-label{font-size:12px;color:var(--muted)}
.stat-value{font-size:27px;font-weight:800;margin-top:12px}
.welcome{
 padding:30px;background:var(--surface);border:1px solid var(--border);
 border-radius:12px;
}
.welcome p{max-width:620px;color:var(--muted);font-size:14px}
.section-heading{
 display:flex;align-items:flex-end;justify-content:space-between;
 gap:15px;margin:30px 0 15px;
}
.section-heading h2{margin:0}
.topic-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:15px}
.topic-card{
 padding:22px;transition:border-color .15s,transform .15s;
}
.topic-card:hover{border-color:var(--primary);transform:translateY(-2px)}
.topic-card-top{display:flex;justify-content:space-between;align-items:center;gap:10px}
.topic-card p{font-size:12px;color:var(--muted);min-height:38px}
.topic-count{font-size:12px;color:var(--muted);margin:18px 0 14px}
.topic-card-footer{
 border-top:1px solid var(--border);padding-top:14px;
 display:flex;justify-content:space-between;align-items:center;
}
.bank-header{
 display:flex;justify-content:space-between;align-items:flex-start;
 gap:15px;margin-bottom:22px;
}
.bank-header p{margin:7px 0 0;color:var(--muted);font-size:13px}
.bank-toolbar{
 display:flex;gap:10px;align-items:center;flex-wrap:wrap;
 margin:20px 0;
}
.search-box{
 flex:1;min-width:210px;padding:12px 14px;
 border:1px solid var(--border);border-radius:7px;
 background:var(--surface);color:var(--text);outline:none;
}
.search-box:focus{border-color:var(--primary)}
.topic-screen{display:none}
.level-panel{
 padding:25px;margin-bottom:20px;
}
.level-grid{display:grid;grid-template-columns:1fr 1fr;gap:13px;margin-top:19px}
.level-card{
 border:1px solid var(--border);background:var(--surface);
 color:var(--text);border-radius:9px;padding:19px;text-align:left;
}
.level-card:hover{border-color:var(--primary);background:var(--primary-light)}
.level-card strong{font-size:17px;display:block;margin-bottom:8px}
.level-card span{font-size:12px;color:var(--muted)}
.level-card .level-count{display:block;font-size:12px;color:var(--primary);font-weight:750;margin-top:13px}
.question-layout{
 display:grid;grid-template-columns:minmax(0,2fr) minmax(260px,.75fr);
 gap:18px;align-items:start;width:100%;
}
.question-main{padding:27px;min-width:0}
.question-top{
 display:flex;align-items:center;justify-content:space-between;
 flex-wrap:wrap;gap:12px;border-bottom:1px solid var(--border);
 padding-bottom:17px;
}
.question-meta{display:flex;align-items:center;gap:10px;flex-wrap:wrap}
.question-number{font-size:11px;color:var(--muted);font-weight:750;letter-spacing:.5px}
.question-text{
 font-family:Georgia,"Times New Roman",serif;
 font-size:21px;line-height:1.75;white-space:pre-line;
 margin:27px 0;
}
.options{display:grid;gap:10px}
.option{
 display:flex;align-items:flex-start;gap:13px;padding:14px;
 border:1px solid var(--border);border-radius:8px;
 cursor:pointer;line-height:1.6;font-size:15px;
 background:var(--surface);transition:.12s;
}
.option:hover{border-color:var(--primary)}
.option.selected{border:1.5px solid var(--primary);background:var(--primary-light);padding:13.5px}
.option.correct{border-color:var(--green);background:var(--green-bg)}
.option.incorrect{border-color:var(--red);background:var(--red-bg)}
.option-letter{
 width:28px;height:28px;display:grid;place-items:center;
 border-radius:5px;background:var(--surface2);
 font-size:12px;font-weight:800;flex-shrink:0;
}
.answer-feedback{
 display:none;margin-top:19px;padding:16px;
 border-radius:8px;font-size:13px;line-height:1.7;
}
.answer-feedback.show{display:block}
.answer-feedback.correct{background:var(--green-bg);color:var(--green)}
.answer-feedback.incorrect{background:var(--red-bg);color:var(--red)}
.explanation{
 display:none;margin-top:12px;padding:18px;
 background:var(--surface2);border:1px solid var(--border);
 border-radius:8px;
}
.explanation.show{display:block}
.explanation p{font-size:13px;line-height:1.8;margin:7px 0}
.further-explanation{
 display:none;margin-top:12px;padding:15px;
 border-left:3px solid var(--primary);
 background:var(--primary-light);border-radius:0 7px 7px 0;
}
.further-explanation.show{display:block}
.question-actions{
 display:flex;justify-content:space-between;align-items:center;
 gap:12px;flex-wrap:wrap;margin-top:23px;padding-top:18px;
 border-top:1px solid var(--border);
}
.question-side{display:grid;gap:14px}
.side-card{padding:21px}
.side-card h3{margin-bottom:15px}
.side-number{font-size:29px;font-weight:800;margin:10px 0}
.progress-track{height:6px;background:var(--border);border-radius:9px;overflow:hidden}
.progress-fill{height:100%;background:var(--primary);width:0%}
.navigator{display:grid;grid-template-columns:repeat(5,1fr);gap:7px}
.navigator button{
 padding:10px 4px;border:1px solid var(--border);
 background:var(--surface);color:var(--text);border-radius:6px;font-size:12px;
}
.navigator button.current{border:2px solid var(--primary);color:var(--primary)}
.navigator button.done{background:var(--green-bg);border-color:var(--green)}
.back-link{
 border:0;background:transparent;color:var(--primary);
 font-size:13px;font-weight:700;padding:0;
}
.coming-card{
 padding:55px 25px;text-align:center;max-width:700px;margin:30px auto;
}
.coming-icon{
 width:60px;height:60px;border-radius:15px;
 background:var(--primary-light);color:var(--primary);
 display:grid;place-items:center;font-size:26px;margin:0 auto 20px;
}
.login-screen{
 min-height:100vh;display:grid;place-items:center;padding:20px;
}
.login-card{
 width:min(420px,100%);padding:35px;
 background:var(--surface);border:1px solid var(--border);border-radius:13px;
}
.login-card input{
 width:100%;padding:13px;border:1px solid var(--border);
 border-radius:7px;background:var(--bg);color:var(--text);margin:9px 0 17px;
}
.login-card button{width:100%}
.mobile-menu{display:none}
.empty{padding:30px;text-align:center;color:var(--muted);font-size:13px}
@media(max-width:1050px){
 .main{padding:25px 23px}
 .question-layout{grid-template-columns:minmax(0,1.6fr) minmax(230px,.8fr)}
 .stat-grid{grid-template-columns:repeat(2,1fr)}
}
@media(max-width:760px){
 .sidebar{transform:translateX(-100%);transition:.2s}
 .sidebar.open{transform:translateX(0)}
 .main{margin-left:0;width:100%;padding:20px 14px 50px}
 .mobile-menu{display:block}
 .topic-grid{grid-template-columns:1fr}
 .question-layout{grid-template-columns:1fr}
 .question-side{grid-template-columns:1fr 1fr}
 .question-main{padding:18px}
 .question-text{font-size:18px}
 .level-grid{grid-template-columns:1fr}
 .bank-header{flex-direction:column}
 .stat-grid{grid-template-columns:1fr 1fr}
}
@media(max-width:430px){
 .question-side{grid-template-columns:1fr}
 .stat-grid{grid-template-columns:1fr 1fr}
}
</style>
</head>
<body>

<!-- LOGIN -->
<div class="login-screen" id="loginScreen">
 <div class="login-card">
  <div class="brand" style="padding:0 0 25px">
   <span class="brand-icon">S</span>SATboost
  </div>
  <div class="eyebrow">YOUR SAT PREPARATION SPACE</div>
  <h1 style="font-size:25px">Welcome back</h1>
  <p class="muted">Sign in to continue your SAT preparation.</p>
  <form id="loginForm">
   <label class="muted">Email address</label>
   <input type="email" id="emailInput" placeholder="you@example.com" required>
   <button class="btn btn-primary">Continue →</button>
  </form>
  <p class="muted" style="font-size:11px">This is currently a browser-based prototype. Email verification is not enabled yet.</p>
 </div>
</div>

<!-- APPLICATION -->
<div class="app" id="app">
 <aside class="sidebar" id="sidebar">
  <div class="brand">
   <span class="brand-icon">S</span>SATboost
  </div>

  <div class="nav-heading">STUDY</div>
  <button class="nav-btn active" data-page="dashboard"><span class="nav-icon">▦</span>Dashboard</button>
  <button class="nav-btn" data-page="bank"><span class="nav-icon">▤</span>Question Bank</button>

  <div class="nav-heading">SUBJECTS</div>
  <button class="nav-btn" data-page="math"><span class="nav-icon">∑</span>Math</button>
  <button class="nav-btn" data-page="reading"><span class="nav-icon">▤</span>Reading</button>
  <button class="nav-btn" data-page="writing"><span class="nav-icon">✎</span>Writing</button>

  <div class="nav-heading">YOUR PROGRESS</div>
  <button class="nav-btn" data-page="mistakes"><span class="nav-icon">↻</span>My Mistakes</button>
  <button class="nav-btn" data-page="saved"><span class="nav-icon">☆</span>Saved Questions</button>
  <button class="nav-btn" data-page="data"><span class="nav-icon">▥</span>My Data</button>
  <button class="nav-btn" data-page="materials"><span class="nav-icon">▧</span>Study Materials</button>

  <div class="sidebar-bottom">
   <button class="nav-btn" id="themeBtn"><span class="nav-icon">◐</span>Toggle theme</button>
   <button class="nav-btn" id="logoutBtn"><span class="nav-icon">⇥</span>Log out</button>
   <div class="profile">
    <div class="avatar" id="avatar">S</div>
    <div>
     <div class="profile-email" id="profileEmail">Student</div>
     <div class="profile-role">SATboost student</div>
    </div>
   </div>
  </div>
 </aside>

 <main class="main">
  <header class="topbar">
   <div class="topbar-left">
    <button class="btn mobile-menu" id="mobileMenu">☰</button>
    <div>
     <div class="eyebrow" id="pageEyebrow">YOUR STUDY SPACE</div>
     <h1 id="pageTitle">Dashboard</h1>
    </div>
   </div>
   <div class="btn-row">
    <button class="btn" id="fontDown">A−</button>
    <button class="btn" id="fontUp">A+</button>
   </div>
  </header>

  <!-- DASHBOARD -->
  <section class="page active" id="page-dashboard">
   <div class="welcome">
    <div class="eyebrow">WELCOME TO SATBOOST</div>
    <h2 style="font-size:27px">Prepare smarter. Achieve more.</h2>
    <p>Your SAT preparation workspace. Practice by skill, understand your mistakes, and follow your progress.</p>
    <button class="btn btn-primary" onclick="showPage('bank')">Explore Question Bank →</button>
   </div>

   <div class="stat-grid">
    <div class="card stat-card"><div class="stat-label">Questions answered</div><div class="stat-value" id="totalAnswered">0</div></div>
    <div class="card stat-card"><div class="stat-label">Correct answers</div><div class="stat-value" id="totalCorrect">0</div></div>
    <div class="card stat-card"><div class="stat-label">Accuracy</div><div class="stat-value" id="accuracy">—</div></div>
    <div class="card stat-card"><div class="stat-label">Saved questions</div><div class="stat-value" id="savedTotal">0</div></div>
   </div>

   <div class="section-heading"><h2>Question Bank</h2><span class="muted">Choose a subject to begin</span></div>
   <div class="topic-grid">
    <div class="card topic-card">
     <div class="topic-card-top"><h2>Math</h2><span class="tag">COMING SOON</span></div>
     <p>Algebra, Advanced Math, Problem-Solving and Data Analysis, Geometry and Trigonometry.</p>
     <div class="topic-card-footer"><span class="muted">Question bank in progress</span><button class="btn" onclick="showPage('math')">Explore →</button></div>
    </div>
    <div class="card topic-card">
     <div class="topic-card-top"><h2>Reading</h2><span class="tag">COMING SOON</span></div>
     <p>Information and Ideas, Craft and Structure, and other reading skills.</p>
     <div class="topic-card-footer"><span class="muted">Question bank in progress</span><button class="btn" onclick="showPage('reading')">Explore →</button></div>
    </div>
    <div class="card topic-card">
     <div class="topic-card-top"><h2>Writing</h2><span class="tag">AVAILABLE</span></div>
     <p>Practice the four Writing skill categories with Medium and Hard questions.</p>
     <div class="topic-card-footer"><span class="muted" id="writingCountHome">8 sample questions</span><button class="btn btn-primary" onclick="showPage('bank')">Start →</button></div>
    </div>
   </div>
  </section>

  <!-- QUESTION BANK -->
  <section class="page" id="page-bank">
   <div id="bankHome">
    <div class="bank-header">
     <div>
      <div class="eyebrow">SAT QUESTION BANK</div>
      <h2 style="font-size:25px">Choose your section</h2>
      <p>Select a skill to practice. Choose your difficulty level on the next screen.</p>
     </div>
     <span class="tag">WRITING</span>
    </div>

    <div class="bank-toolbar">
     <input class="search-box" id="topicSearch" placeholder="Search skills...">
     <span class="muted" id="totalBankCount">8 questions available</span>
    </div>

    <div class="topic-grid" id="topicCards"></div>
   </div>

   <!-- LEVEL SELECTION -->
   <div class="topic-screen" id="levelScreen">
    <button class="back-link" onclick="backToBank()">← Back to all sections</button>
    <div class="section-heading">
     <div>
      <div class="eyebrow">WRITING QUESTION BANK</div>
      <h2 id="levelTopicTitle">Boundaries</h2>
      <p class="muted">Choose the difficulty level you want to practice.</p>
     </div>
     <span class="tag" id="levelTotal">2 QUESTIONS</span>
    </div>

    <div class="level-panel card">
     <h2>Select difficulty</h2>
     <p class="muted">Each level has its own question set and progress.</p>
     <div class="level-grid">
      <button class="level-card" onclick="startTopic('Medium')">
       <strong>Medium</strong>
       <span>Build your understanding and strengthen your skills.</span>
       <span class="level-count" id="mediumCount">2 questions →</span>
      </button>
      <button class="level-card" onclick="startTopic('Hard')">
       <strong>Hard</strong>
       <span>Challenge yourself with more demanding questions.</span>
       <span class="level-count" id="hardCount">2 questions →</span>
      </button>
     </div>
    </div>
   </div>

   <!-- QUESTION VIEW -->
   <div class="topic-screen" id="questionScreen">
    <div class="bank-header">
     <div>
      <button class="back-link" onclick="backToLevels()">← Back to difficulty levels</button>
      <div class="eyebrow" style="margin-top:15px">QUESTION BANK / <span id="crumbTopic">BOUNDARIES</span></div>
      <h2 id="questionPageTitle">Boundaries — Medium</h2>
      <p id="questionPageSubtitle">Practice questions</p>
     </div>
     <span class="tag" id="difficultyTag">MEDIUM</span>
    </div>

    <div class="question-layout">
     <div class="card question-main">
      <div class="question-top">
       <div class="question-meta">
        <span class="tag" id="questionTopicTag">Boundaries</span>
        <span class="muted" id="questionDifficulty">Medium</span>
       </div>
       <button class="btn" id="saveQuestionBtn">☆ Save</button>
      </div>

      <div class="question-number" id="questionNumber" style="margin-top:24px">QUESTION 1 OF 2</div>
      <div class="question-text" id="questionText"></div>
      <div class="options" id="answerOptions"></div>

      <div class="answer-feedback" id="answerFeedback"></div>

      <div class="explanation" id="explanationBox">
       <h3>Explanation</h3>
       <p id="explanationText"></p>
       <button class="btn btn-light" id="furtherBtn" onclick="toggleFurther()">Further Explanation ↓</button>
       <div class="further-explanation" id="furtherBox">
        <h3>Further Explanation</h3>
        <p id="furtherText"></p>
       </div>
      </div>

      <div class="question-actions">
       <button class="btn" id="previousQuestionBtn" onclick="previousQuestion()">← Previous</button>
       <div class="btn-row">
        <button class="btn btn-primary" id="checkAnswerBtn" onclick="checkAnswer()">Check Answer</button>
        <button class="btn btn-primary" id="nextQuestionBtn" onclick="nextQuestion()" style="display:none">Next →</button>
       </div>
      </div>
     </div>

     <div class="question-side">
      <div class="card side-card">
       <h3>Question progress</h3>
       <div class="side-number" id="progressNumber">0/2</div>
       <div class="progress-track"><div class="progress-fill" id="progressFill"></div></div>
       <p class="muted" id="progressCaption">Questions you have answered.</p>
      </div>

      <div class="card side-card">
       <h3>Question navigator</h3>
       <div class="navigator" id="questionNavigator"></div>
       <p class="muted" style="margin-bottom:0">Green means answered.</p>
      </div>

      <div class="card side-card">
       <h3>Study tip</h3>
       <p class="muted">Read the entire sentence carefully. Think about the relationship between its ideas before choosing an answer.</p>
      </div>
     </div>
    </div>
   </div>
  </section>

  <!-- COMING SOON PAGES -->
  <section class="page" id="page-math">
   <div class="card coming-card">
    <div class="coming-icon">∑</div>
    <div class="eyebrow">SAT MATH</div>
    <h2>Math Question Bank</h2>
    <p class="muted">Coming Soon. We are preparing the Math question bank.</p>
    <span class="tag">COMING SOON</span>
   </div>
  </section>

  <section class="page" id="page-reading">
   <div class="card coming-card">
    <div class="coming-icon">▤</div>
    <div class="eyebrow">SAT READING</div>
    <h2>Reading Question Bank</h2>
    <p class="muted">Coming Soon. We are preparing the Reading question bank.</p>
    <span class="tag">COMING SOON</span>
   </div>
  </section>

  <section class="page" id="page-writing">
   <div class="card coming-card">
    <div class="coming-icon">✎</div>
    <div class="eyebrow">SAT WRITING</div>
    <h2>Writing Question Bank</h2>
    <p class="muted">Practice Writing questions by skill and difficulty.</p>
    <button class="btn btn-primary" onclick="showPage('bank')">Open Writing Question Bank →</button>
   </div>
  </section>

  <!-- MISTAKES -->
  <section class="page" id="page-mistakes">
   <div class="card" style="padding:25px">
    <h2>My Mistakes</h2>
    <p class="muted">Questions you answered incorrectly.</p>
    <div id="mistakesList"></div>
   </div>
  </section>

  <!-- SAVED -->
  <section class="page" id="page-saved">
   <div class="card" style="padding:25px">
    <h2>Saved Questions</h2>
    <p class="muted">Questions you have bookmarked for later.</p>
    <div id="savedList"></div>
   </div>
  </section>

  <!-- DATA -->
  <section class="page" id="page-data">
   <div class="card" style="padding:25px">
    <h2>My Data</h2>
    <p class="muted">Your question practice statistics.</p>
    <div class="stat-grid">
     <div><div class="stat-label">Answered</div><div class="stat-value" id="dataAnswered">0</div></div>
     <div><div class="stat-label">Correct</div><div class="stat-value" id="dataCorrect">0</div></div>
     <div><div class="stat-label">Incorrect</div><div class="stat-value" id="dataWrong">0</div></div>
     <div><div class="stat-label">Accuracy</div><div class="stat-value" id="dataAccuracy">—</div></div>
    </div>
    <div id="dataTopics"></div>
   </div>
  </section>

  <!-- MATERIALS -->
  <section class="page" id="page-materials">
   <div class="card" style="padding:25px">
    <h2>Study Materials</h2>
    <div class="topic-grid" style="margin-top:20px">
     <div class="card topic-card"><h3>College Board</h3><p>Official SAT information and resources.</p><a href="https://satsuite.collegeboard.org/" target="_blank">Visit website →</a></div>
     <div class="card topic-card"><h3>Bluebook</h3><p>Official digital testing application.</p><a href="https://bluebook.collegeboard.org/" target="_blank">Visit website →</a></div>
     <div class="card topic-card"><h3>Khan Academy</h3><p>Free SAT preparation resources.</p><a href="https://www.khanacademy.org/test-prep/sat" target="_blank">Visit website →</a></div>
     <div class="card topic-card"><h3>Official Question Bank</h3><p>College Board practice questions.</p><a href="https://satsuitequestionbank.collegeboard.org/" target="_blank">Visit website →</a></div>
    </div>
   </div>
  </section>
 </main>
</div>

<script>
/* ==========================================
   SATBOOST QUESTION BANK
   ========================================== */

const topics = [
 "Boundaries",
 "Form, Structure & Sense",
 "Transitions",
 "Rhetorical Synthesis"
];

/*
  These are original sample questions.
  Medium and Hard currently use the same question set.
  Later, each level can have its own question array.
*/

const questionBank = {
 "Boundaries": [
  {
   id:"B1",
   difficulty:"Medium",
   text:"The research team collected data from several coastal regions ____ the results revealed a clear pattern in water temperature.",
   options:[
    "regions, and the",
    "regions; the",
    "regions the",
    "regions, the"
   ],
   answer:1,
   explanation:"The sentence contains two independent clauses. A semicolon can connect two closely related independent clauses.",
   further:"The first independent clause is “The research team collected data from several coastal regions.” The second is “the results revealed a clear pattern in water temperature.” Both clauses can stand alone as complete sentences. A semicolon is therefore appropriate between them. A comma alone would create a comma splice."
  },
  {
   id:"B2",
   difficulty:"Medium",
   text:"Although the experiment was initially considered unsuccessful ____ the researchers later discovered an important result.",
   options:[
    "unsuccessful,",
    "unsuccessful;",
    "unsuccessful",
    "unsuccessful:"
   ],
   answer:0,
   explanation:"An introductory dependent clause is followed by a comma.",
   further:"The word “Although” introduces a dependent clause. This clause cannot stand alone as a complete sentence. When an introductory dependent clause comes before the main clause, a comma separates the two parts. A semicolon is not used here."
  },
  {
   id:"B3",
   difficulty:"Medium",
   text:"The university's new research center ____ which opened last September, focuses on renewable energy.",
   options:[
    "building",
    "building,",
    "building;",
    "building:"
   ],
   answer:1,
   explanation:"The nonessential descriptive clause is set off with commas.",
   further:"The phrase “which opened last September” adds extra information about the research center. The sentence remains grammatically complete without it. Nonessential information beginning with “which” is generally enclosed by commas."
  }
 ],
 "Form, Structure & Sense": [
  {
   id:"F1",
   difficulty:"Medium",
   text:"The collection of rare plants ____ carefully maintained by the university's biology department.",
   options:["are","were","is","have been"],
   answer:2,
   explanation:"The subject “collection” is singular, so it takes the singular verb “is.”",
   further:"The main subject is “collection,” not “plants.” The phrase “of rare plants” describes the collection but does not change the subject's number. This is why “is” is correct."
  },
  {
   id:"F2",
   difficulty:"Medium",
   text:"By the time the final report was published, the scientists ____ the data for nearly three years.",
   options:["analyze","had been analyzing","will analyze","are analyzing"],
   answer:1,
   explanation:"The past perfect progressive describes an activity that continued before another event in the past.",
   further:"The report was published at a specific point in the past. The scientists' analysis had already been continuing for nearly three years before that point. The past perfect progressive form “had been analyzing” communicates this timeline."
  }
 ],
 "Transitions": [
  {
   id:"T1",
   difficulty:"Medium",
   text:"The first design was inexpensive to produce. ____, it required frequent repairs, making it costly over time.",
   options:["For example","Nevertheless","Similarly","In addition"],
   answer:1,
   explanation:"“Nevertheless” introduces a contrast between the low initial cost and later repair expenses.",
   further:"The two sentences present contrasting information. The first says the design was inexpensive to produce, while the second explains that frequent repairs made it costly over time. “Nevertheless” signals that contrast."
  },
  {
   id:"T2",
   difficulty:"Medium",
   text:"Several studies have examined the effects of urban green spaces on air quality. ____, recent research has also explored their influence on residents' mental well-being.",
   options:["In contrast","As a result","Furthermore","Instead"],
   answer:2,
   explanation:"“Furthermore” adds another related point.",
   further:"Both sentences discuss research into the benefits of urban green spaces. The second sentence adds another area of research rather than presenting a contrast or a consequence. “Furthermore” is therefore the best transition."
  }
 ],
 "Rhetorical Synthesis": [
  {
   id:"R1",
   difficulty:"Medium",
   text:"A student is writing about a museum exhibition. The student wants to emphasize that the exhibition includes works from different historical periods.\n\nNotes:\n• The exhibition opened in 2024.\n• It contains 60 paintings.\n• The paintings were created between 1600 and 1950.\n• The exhibition is located in the city art museum.\n\nWhich choice most effectively uses the notes to achieve the student's goal?",
   options:[
    "The city art museum opened an exhibition in 2024.",
    "The exhibition features 60 paintings created across a period spanning from 1600 to 1950.",
    "The museum is located in the city center.",
    "Sixty paintings are included in the exhibition."
   ],
   answer:1,
   explanation:"This choice emphasizes the different historical periods represented by the paintings.",
   further:"The student's goal is specifically to emphasize the range of historical periods. Choice B includes the dates 1600 and 1950, directly communicating that range. The other choices mention facts from the notes but do not achieve the stated purpose."
  },
  {
   id:"R2",
   difficulty:"Medium",
   text:"A student is writing about a scientific discovery. The student wants to compare the two methods used in the study.\n\nNotes:\n• Method A took 12 hours to complete.\n• Method B took 4 hours to complete.\n• Both methods produced results with similar accuracy.\n\nWhich choice best achieves the student's goal?",
   options:[
    "The study used two methods to collect scientific data.",
    "Method A and Method B both produced accurate results.",
    "Although Method A took longer, both methods achieved similar levels of accuracy.",
    "Method B was used in a scientific study."
   ],
   answer:2,
   explanation:"This choice compares the time required by each method while highlighting their similar accuracy.",
   further:"The prompt asks for a comparison. Choice C includes both the difference in completion time and the similarity in accuracy. This directly combines the most relevant notes to accomplish the student's purpose."
  }
 ]
};

/* App state */
let currentUser=localStorage.getItem("satboost_email")||"";
let currentPage="dashboard";
let currentTopic="";
let currentLevel="Medium";
let currentQuestions=[];
let currentIndex=0;
let selectedAnswer=null;
let checked=false;
let fontSize=21;

let userAnswers=JSON.parse(localStorage.getItem("satboost_answers")||"{}");
let savedQuestions=JSON.parse(localStorage.getItem("satboost_saved")||"[]");

const $=id=>document.getElementById(id);

function saveData(){
 localStorage.setItem("satboost_answers",JSON.stringify(userAnswers));
 localStorage.setItem("satboost_saved",JSON.stringify(savedQuestions));
}

function allQuestions(){
 return topics.flatMap(topic=>
  (questionBank[topic]||[]).map(q=>({...q,topic}))
 );
}

function questionsForLevel(topic,level){
 return (questionBank[topic]||[]).map(q=>({...q,topic,difficulty:level}));
}

/* Login */
function initialize(){
 if(!currentUser){
  $("loginScreen").style.display="grid";
  $("app").style.display="none";
  return;
 }
 $("loginScreen").style.display="none";
 $("app").style.display="flex";
 $("profileEmail").textContent=currentUser;
 $("avatar").textContent=currentUser.charAt(0).toUpperCase();
 renderAll();
}

$("loginForm").addEventListener("submit",e=>{
 e.preventDefault();
 currentUser=$("emailInput").value.trim().toLowerCase();
 localStorage.setItem("satboost_email",currentUser);
 initialize();
});

$("logoutBtn").onclick=()=>{
 localStorage.removeItem("satboost_email");
 currentUser="";
 initialize();
};

/* Theme */
if(localStorage.getItem("satboost_theme")==="dark"){
 document.body.classList.add("dark");
}
$("themeBtn").onclick=()=>{
 document.body.classList.toggle("dark");
 localStorage.setItem(
  "satboost_theme",
  document.body.classList.contains("dark")?"dark":"light"
 );
};

/* Font size */
$("fontUp").onclick=()=>{
 fontSize=Math.min(28,fontSize+1);
 document.documentElement.style.setProperty("--question-font",fontSize+"px");
 document.querySelectorAll(".question-text").forEach(el=>el.style.fontSize=fontSize+"px");
};
$("fontDown").onclick=()=>{
 fontSize=Math.max(16,fontSize-1);
 document.querySelectorAll(".question-text").forEach(el=>el.style.fontSize=fontSize+"px");
};

/* Navigation */
const pageTitles={
 dashboard:"Dashboard",
 bank:"Question Bank",
 math:"Math",
 reading:"Reading",
 writing:"Writing",
 mistakes:"My Mistakes",
 saved:"Saved Questions",
 data:"My Data",
 materials:"Study Materials"
};

function showPage(page){
 currentPage=page;
 document.querySelectorAll(".page").forEach(el=>el.classList.remove("active"));
 $("page-"+page).classList.add("active");
 $("pageTitle").textContent=pageTitles[page];
 $("pageEyebrow").textContent=page==="bank"?"SAT QUESTION BANK":"YOUR STUDY SPACE";

 document.querySelectorAll("[data-page]").forEach(btn=>{
  btn.classList.toggle("active",btn.dataset.page===page);
 });

 $("sidebar").classList.remove("open");

 if(page==="dashboard")renderDashboard();
 if(page==="bank")backToBank();
 if(page==="mistakes")renderMistakes();
 if(page==="saved")renderSaved();
 if(page==="data")renderData();
}

document.querySelectorAll("[data-page]").forEach(btn=>{
 btn.addEventListener("click",()=>showPage(btn.dataset.page));
});

$("mobileMenu").onclick=()=>$("sidebar").classList.toggle("open");

/* Dashboard */
function getStats(){
 const list=Object.values(userAnswers);
 const correct=list.filter(x=>x.correct).length;
 return {
  answered:list.length,
  correct,
  wrong:list.length-correct,
  accuracy:list.length?Math.round(correct/list.length*100):0
 };
}

function renderDashboard(){
 const s=getStats();
 $("totalAnswered").textContent=s.answered;
 $("totalCorrect").textContent=s.correct;
 $("accuracy").textContent=s.answered?s.accuracy+"%":"—";
 $("savedTotal").textContent=savedQuestions.length;
 $("writingCountHome").textContent=allQuestions().length+" sample questions";
}

/* Question Bank home */
function backToBank(){
 $("bankHome").style.display="block";
 $("levelScreen").style.display="none";
 $("questionScreen").style.display="none";
 renderTopicCards();
}

function renderTopicCards(){
 const search=$("topicSearch").value.toLowerCase();
 const total=allQuestions().length;
 $("totalBankCount").textContent=total+" sample questions available";

 $("topicCards").innerHTML=topics
 .filter(t=>t.toLowerCase().includes(search))
 .map(topic=>{
  const count=questionBank[topic].length;
  return `
   <div class="card topic-card">
    <div class="topic-card-top">
     <h2>${topic}</h2>
     <span class="tag">WRITING</span>
    </div>
    <p>Practice ${topic} questions. Select your difficulty level to begin.</p>
    <div class="topic-card-footer">
     <span class="topic-count">${count} questions in each level</span>
     <button class="btn btn-primary" onclick="openTopic('${topic}')">Open section →</button>
    </div>
   </div>
  `;
 }).join("")||'<div class="empty">No sections found.</div>';
}

$("topicSearch").addEventListener("input",renderTopicCards);

function openTopic(topic){
 currentTopic=topic;
 $("bankHome").style.display="none";
 $("levelScreen").style.display="block";
 $("questionScreen").style.display="none";
 $("levelTopicTitle").textContent=topic;

 const count=questionBank[topic].length;
 $("levelTotal").textContent=count+" QUESTIONS";
 $("mediumCount").textContent=count+" questions →";
 $("hardCount").textContent=count+" questions →";
}

function backToLevels(){
 $("levelScreen").style.display="block";
 $("questionScreen").style.display="none";
}

function startTopic(level){
 currentLevel=level;
 currentQuestions=questionsForLevel(currentTopic,level);
 currentIndex=0;
 selectedAnswer=null;
 checked=false;

 $("levelScreen").style.display="none";
 $("questionScreen").style.display="block";
 $("questionPageTitle").textContent=currentTopic+" — "+level;
 $("questionPageSubtitle").textContent=currentQuestions.length+" questions · No time limit";
 $("crumbTopic").textContent=currentTopic.toUpperCase();
 $("difficultyTag").textContent=level.toUpperCase();

 renderQuestion();
}

/* Question rendering */
function currentQuestion(){
 return currentQuestions[currentIndex];
}

function answerKey(q){
 return q.id+"_"+currentLevel;
}

function renderQuestion(){
 const q=currentQuestion();
 if(!q)return;

 const key=answerKey(q);
 const previous=userAnswers[key];

 selectedAnswer=previous?previous.choice:null;
 checked=!!previous;

 $("questionTopicTag").textContent=currentTopic;
 $("questionDifficulty").textContent=currentLevel;
 $("questionNumber").textContent="QUESTION "+(currentIndex+1)+" OF "+currentQuestions.length;
 $("questionText").textContent=q.text;
 $("questionText").style.fontSize=fontSize+"px";

 $("saveQuestionBtn").textContent=
  savedQuestions.includes(key)?"★ Saved":"☆ Save";

 $("saveQuestionBtn").onclick=()=>toggleSave(key);

 $("answerOptions").innerHTML=q.options.map((option,i)=>{
  let cls="";
  if(checked&&i===q.answer)cls="correct";
  else if(checked&&i===selectedAnswer&&i!==q.answer)cls="incorrect";
  else if(!checked&&i===selectedAnswer)cls="selected";

  return `
   <div class="option ${cls}" onclick="chooseAnswer(${i})">
    <span class="option-letter">${"ABCD"[i]}</span>
    <span>${option}</span>
   </div>
  `;
 }).join("");

 $("answerFeedback").className="answer-feedback";
 $("explanationBox").classList.remove("show");
 $("furtherBox").classList.remove("show");

 if(checked){
  showExplanation(q,previous);
 }

 $("checkAnswerBtn").style.display=checked?"none":"inline-block";
 $("nextQuestionBtn").style.display=checked?"inline-block":"none";
 $("previousQuestionBtn").disabled=currentIndex===0;

 renderNavigator();
 renderProgress();
}

function chooseAnswer(index){
 if(checked)return;
 selectedAnswer=index;
 document.querySelectorAll(".option").forEach((el,i)=>{
  el.classList.toggle("selected",i===index);
 });
}

function checkAnswer(){
 if(selectedAnswer===null){
  alert("Please select an answer first.");
  return;
 }

 const q=currentQuestion();
 const key=answerKey(q);
 const correct=selectedAnswer===q.answer;

 userAnswers[key]={
  choice:selectedAnswer,
  correct:correct,
  topic:currentTopic,
  level:currentLevel,
  questionId:q.id
 };

 saveData();
 checked=true;
 renderQuestion();
 renderDashboard();
}

function showExplanation(q,previous){
 const correct=previous.correct;
 $("answerFeedback").className="answer-feedback show "+(correct?"correct":"incorrect");
 $("answerFeedback").innerHTML=correct
  ?"<strong>✓ Correct!</strong> Your answer is correct."
  :"<strong>✕ Incorrect.</strong> The correct answer is <b>"+ "ABCD"[q.answer] +"</b>.";

 $("explanationBox").classList.add("show");
 $("explanationText").textContent=q.explanation;
 $("furtherText").textContent=q.further||q.explanation;
 $("furtherBox").classList.remove("show");
 $("furtherBtn").textContent="Further Explanation ↓";
}

function toggleFurther(){
 const box=$("furtherBox");
 const open=box.classList.toggle("show");
 $("furtherBtn").textContent=open?"Hide Further Explanation ↑":"Further Explanation ↓";
}

function nextQuestion(){
 if(currentIndex<currentQuestions.length-1){
  currentIndex++;
  renderQuestion();
 }else{
  const correct=currentQuestions.filter(q=>{
   const a=userAnswers[answerKey(q)];
   return a&&a.correct;
  }).length;

  alert(
   "Section completed!\n\n"+
   "Questions: "+currentQuestions.length+
   "\nCorrect: "+correct+
   "\nIncorrect: "+(currentQuestions.length-correct)
  );

  backToLevels();
 }
}

function previousQuestion(){
 if(currentIndex>0){
  currentIndex--;
  renderQuestion();
 }
}

function goToQuestion(index){
 currentIndex=index;
 renderQuestion();
}

function renderNavigator(){
 $("questionNavigator").innerHTML=currentQuestions.map((q,i)=>{
  const a=userAnswers[answerKey(q)];
  return `
   <button
    class="${i===currentIndex?"current ":""}${a?"done":""}"
    onclick="goToQuestion(${i})">${i+1}</button>
  `;
 }).join("");
}

function renderProgress(){
 const answered=currentQuestions.filter(q=>userAnswers[answerKey(q)]).length;
 const total=currentQuestions.length;
 $("progressNumber").textContent=answered+"/"+total;
 $("progressFill").style.width=(answered/total*100)+"%";
 $("progressCaption").textContent="Questions you have answered.";
}

/* Save questions */
function toggleSave(key){
 if(savedQuestions.includes(key)){
  savedQuestions=savedQuestions.filter(x=>x!==key);
 }else{
  savedQuestions.push(key);
 }
 saveData();
 $("saveQuestionBtn").textContent=
  savedQuestions.includes(key)?"★ Saved":"☆ Save";
 renderDashboard();
}

/* Mistakes */
function renderMistakes(){
 const wrong=allQuestions().flatMap(q=>
  ["Medium","Hard"].map(level=>({...q,level}))
 ).filter(q=>{
  const a=userAnswers[q.id+"_"+q.level];
  return a&&!a.correct;
 });

 if(!wrong.length){
  $("mistakesList").innerHTML='<div class="empty">No mistakes yet. Keep practicing!</div>';
  return;
 }

 $("mistakesList").innerHTML=wrong.map(q=>`
  <div class="topic-card" style="border-bottom:1px solid var(--border)">
   <div class="topic-card-top"><b>${q.topic}</b><span class="tag">${q.level}</span></div>
   <p>${q.text.slice(0,150)}${q.text.length>150?"...":""}</p>
   <button class="btn" onclick="openTopic('${q.topic}');startTopic('${q.level}');goToQuestion(${currentQuestions.findIndex(x=>x.id===q.id)})">Review section →</button>
  </div>
 `).join("");
}

/* Saved questions */
function renderSaved(){
 const all=allQuestions();
 const items=savedQuestions.map(key=>{
  const parts=key.split("_");
  const id=parts[0],level=parts[1];
  const q=all.find(x=>x.id===id);
  return q?{...q,level,key}:null;
 }).filter(Boolean);

 $("savedList").innerHTML=items.length?items.map(q=>`
  <div class="topic-card" style="border-bottom:1px solid var(--border)">
   <div class="topic-card-top"><b>${q.topic}</b><span class="tag">${q.level}</span></div>
   <p>${q.text.slice(0,140)}${q.text.length>140?"...":""}</p>
   <button class="btn" onclick="openTopic('${q.topic}');startTopic('${q.level}');">Open section →</button>
   <button class="btn" onclick="toggleSave('${q.key}');renderSaved()">Remove saved</button>
  </div>
 `).join(""):'<div class="empty">You have not saved any questions yet.</div>';
}

/* Data */
function renderData(){
 const s=getStats();
 $("dataAnswered").textContent=s.answered;
 $("dataCorrect").textContent=s.correct;
 $("dataWrong").textContent=s.wrong;
 $("dataAccuracy").textContent=s.answered?s.accuracy+"%":"—";

 $("dataTopics").innerHTML=topics.map(topic=>{
  const qs=questionBank[topic];
  let total=0,correct=0;
  ["Medium","Hard"].forEach(level=>{
   qs.forEach(q=>{
    const a=userAnswers[q.id+"_"+level];
    if(a){total++;if(a.correct)correct++}
   });
  });
  return `
   <div style="padding:17px 0;border-top:1px solid var(--border)">
    <b>${topic}</b>
    <span class="muted" style="float:right">${total} answered · ${correct} correct</span>
   </div>
  `;
 }).join("");
}

function renderAll(){
 renderDashboard();
 renderTopicCards();
}

/* Start */
initialize();
</script>
</body>
</html>
