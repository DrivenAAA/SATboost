
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SATboost — SAT Preparation</title>
<style>
:root{
  --bg:#f5f6f8;
  --surface:#ffffff;
  --surface2:#f8f9fb;
  --text:#182230;
  --muted:#667085;
  --line:#e4e7ec;
  --blue:#3157c8;
  --blue-light:#edf2ff;
  --green:#16845b;
  --red:#c43e48;
  --shadow:0 2px 10px rgba(16,24,40,.035);
}
*{box-sizing:border-box}
html,body{margin:0;width:100%;height:100%;font-family:Arial,Helvetica,sans-serif;background:var(--bg);color:var(--text)}
button,input{font:inherit}
button{cursor:pointer}
#app{height:100vh;width:100%;display:grid;grid-template-columns:250px minmax(0,1fr);overflow:hidden}
.sidebar{
  background:var(--surface);border-right:1px solid var(--line);
  height:100vh;overflow-y:auto;padding:24px 16px 18px;
  display:flex;flex-direction:column;z-index:5
}
.brand{display:flex;align-items:center;gap:12px;padding:2px 10px 34px}
.brand-mark{width:38px;height:38px;background:#3157c8;color:white;border-radius:8px;display:grid;place-items:center;font-size:22px;font-weight:700}
.brand-name{font-size:23px;font-weight:700;letter-spacing:-.7px}
.nav-label{font-size:11px;font-weight:700;letter-spacing:1.4px;color:#8992a3;padding:12px 14px 9px}
.nav-item{
  display:flex;align-items:center;gap:12px;width:100%;border:0;
  padding:12px 14px;margin:2px 0;background:transparent;color:#586579;
  border-radius:6px;text-align:left;font-size:13px;font-weight:600;min-height:43px
}
.nav-item:hover{background:#f5f7fa;color:var(--text)}
.nav-item.active{background:var(--blue-light);color:var(--blue)}
.nav-icon{width:18px;text-align:center;font-size:15px}
.nav-divider{height:1px;background:var(--line);margin:14px 4px}
.sidebar-bottom{margin-top:auto;padding-top:20px}
.user-block{border-top:1px solid var(--line);margin-top:14px;padding:18px 8px 4px;display:flex;gap:10px;align-items:center}
.avatar{width:34px;height:34px;border-radius:50%;background:var(--blue-light);color:var(--blue);display:grid;place-items:center;font-weight:700}
.user-email{font-size:11px;color:var(--muted);overflow-wrap:anywhere}
.user-role{font-size:11px;color:#98a2b3;margin-top:4px}
.main{height:100vh;overflow-y:auto;min-width:0}
.topbar{
  height:66px;background:rgba(255,255,255,.88);border-bottom:1px solid var(--line);
  display:flex;align-items:center;justify-content:space-between;padding:0 38px;
  position:sticky;top:0;z-index:3
}
.breadcrumb{font-size:12px;color:var(--muted)}
.top-actions{display:flex;gap:8px}
.small-btn{border:1px solid var(--line);background:white;color:var(--text);padding:9px 13px;border-radius:6px;font-size:12px}
.small-btn:hover{border-color:#aab6d1}
.content{padding:30px 38px 60px;width:100%;max-width:none}
.page-heading{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:26px}
.eyebrow{font-size:10px;font-weight:700;letter-spacing:1.5px;color:#7d8798;margin-bottom:10px}
h1{font-size:29px;letter-spacing:-.8px;font-weight:600;margin:0}
h2{font-size:20px;font-weight:600;margin:0}
h3{font-size:16px;font-weight:600;margin:0}
.subtitle{color:var(--muted);font-size:13px;margin-top:8px;line-height:1.6}
.panel{background:var(--surface);border:1px solid var(--line);border-radius:9px;box-shadow:var(--shadow)}
.welcome{padding:32px 34px;margin-bottom:22px}
.welcome h2{font-size:25px;letter-spacing:-.5px;margin:12px 0}
.welcome p{color:var(--muted);font-size:14px;line-height:1.7;max-width:760px}
.primary-btn{background:var(--blue);border:1px solid var(--blue);color:white;border-radius:6px;padding:12px 18px;font-size:13px;font-weight:600}
.primary-btn:hover{background:#2447ad}
.secondary-btn{background:white;border:1px solid var(--line);color:var(--text);border-radius:6px;padding:11px 16px;font-size:13px}
.stats{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:14px;margin-bottom:32px}
.stat{padding:20px 22px}
.stat-label{font-size:12px;color:var(--muted)}
.stat-value{font-size:27px;font-weight:650;margin-top:14px}
.section-heading{display:flex;justify-content:space-between;align-items:center;margin:30px 0 15px}
.section-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:15px}
.subject-card{padding:24px;min-height:150px;cursor:pointer;transition:.15s}
.subject-card:hover{border-color:#a9b8e7;transform:translateY(-1px)}
.subject-card .subject-icon{font-size:19px;color:var(--blue);margin-bottom:18px}
.subject-card p{font-size:12px;color:var(--muted);line-height:1.6}
.subject-card .card-foot{font-size:11px;color:var(--blue);font-weight:600;margin-top:18px}
.coming{display:inline-block;font-size:10px;letter-spacing:.5px;font-weight:700;color:#737f91;background:#f0f2f5;padding:5px 8px;border-radius:4px}
.topic-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:16px}
.topic-card{padding:23px 24px;cursor:pointer;transition:.15s}
.topic-card:hover{border-color:#a9b8e7}
.topic-top{display:flex;align-items:center;justify-content:space-between}
.topic-number{font-size:11px;color:#8791a1;letter-spacing:.7px}
.topic-card p{font-size:12px;color:var(--muted);line-height:1.6;margin:10px 0 20px}
.topic-count{font-size:11px;color:var(--muted)}
.level-row{display:flex;gap:10px;margin-top:18px}
.level-btn{background:white;border:1px solid var(--line);border-radius:5px;padding:10px 17px;font-size:12px;color:var(--text)}
.level-btn:hover,.level-btn.selected{background:var(--blue-light);border-color:#9eb1ec;color:var(--blue)}
.bank-toolbar{display:grid;grid-template-columns:minmax(220px,1fr) minmax(180px,260px) minmax(150px,190px);gap:10px;margin-bottom:18px}
.field{height:43px;width:100%;border:1px solid var(--line);background:white;border-radius:6px;padding:0 13px;color:var(--text);outline:none}
.field:focus{border-color:#8ba1e6}
.bank-layout{display:grid;grid-template-columns:minmax(0,1fr) 285px;gap:18px;align-items:start}
.question-panel{padding:27px 29px;min-height:480px}
.question-meta{display:flex;justify-content:space-between;align-items:center;margin-bottom:25px}
.tag{font-size:10px;font-weight:700;color:var(--blue);background:var(--blue-light);padding:6px 9px;border-radius:4px}
.difficulty{font-size:11px;color:var(--muted);margin-left:9px}
.save-btn{border:1px solid var(--line);background:white;padding:9px 12px;border-radius:5px;font-size:12px;color:var(--text)}
.question-number{font-size:10px;color:#8791a1;letter-spacing:.8px;margin-bottom:17px}
.question-text{font-size:17px;line-height:1.8;white-space:pre-line;margin:0 0 24px;max-width:1050px}
.options{display:grid;gap:9px}
.option{
  border:1px solid var(--line);background:white;border-radius:6px;
  display:flex;align-items:center;gap:13px;padding:13px 15px;
  text-align:left;color:var(--text);font-size:13px;line-height:1.5;width:100%
}
.option:hover{border-color:#aab8dc;background:#fafbff}
.option-letter{width:25px;height:25px;display:grid;place-items:center;background:#f2f4f7;border-radius:4px;font-size:11px;font-weight:700;flex-shrink:0}
.option.correct{border-color:#36a879;background:#f0faf5}
.option.incorrect{border-color:#d96a73;background:#fff5f5}
.option:disabled{cursor:default}
.answer-feedback{margin-top:17px;border-radius:6px;padding:15px 17px;font-size:13px;line-height:1.7;display:none}
.answer-feedback.show{display:block}
.answer-feedback.good{background:#effaf4;border:1px solid #b8e5cd;color:#176b4a}
.answer-feedback.bad{background:#fff4f4;border:1px solid #f0c4c7;color:#96353e}
.explanation{margin-top:12px;border-top:1px solid rgba(0,0,0,.08);padding-top:12px}
.further{display:none;margin-top:10px;color:inherit}
.further.show{display:block}
.question-actions{display:flex;align-items:center;gap:9px;flex-wrap:wrap;margin-top:22px}
.question-actions .primary-btn,.question-actions .secondary-btn{padding:10px 16px}
.side-stack{display:grid;gap:14px}
.side-panel{padding:22px}
.side-panel h3{margin-bottom:17px}
.progress-number{font-size:28px;font-weight:700;margin:8px 0 14px}
.progress-track{height:7px;background:#edf0f4;border-radius:8px;overflow:hidden}
.progress-fill{height:100%;background:var(--blue);width:0%;transition:.2s}
.muted-small{font-size:11px;color:var(--muted);line-height:1.6;margin-top:11px}
.navigator{display:grid;grid-template-columns:repeat(5,1fr);gap:7px}
.nav-q{height:35px;border:1px solid var(--line);border-radius:5px;background:white;font-size:11px;color:var(--text)}
.nav-q.current{border-color:var(--blue);background:var(--blue-light);color:var(--blue)}
.nav-q.done{border-color:#9ed7bc;background:#effaf4;color:#176b4a}
.empty-state{padding:45px 24px;text-align:center;color:var(--muted);font-size:13px;line-height:1.8}
.empty-state h3{color:var(--text);margin-bottom:10px}
.data-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:15px}
.data-card{padding:23px}
.data-card p{font-size:12px;color:var(--muted);line-height:1.7}
.list-row{display:flex;justify-content:space-between;align-items:center;padding:15px 0;border-bottom:1px solid var(--line);font-size:13px}
.list-row:last-child{border-bottom:0}
.modal-backdrop{position:fixed;inset:0;background:rgba(15,23,42,.45);z-index:20;display:none;align-items:center;justify-content:center;padding:20px}
.modal-backdrop.show{display:flex}
.modal{background:white;border-radius:9px;padding:30px;max-width:420px;width:100%;box-shadow:0 15px 50px rgba(0,0,0,.16)}
.modal h2{margin-bottom:10px}
.modal p{font-size:13px;color:var(--muted);line-height:1.7}
.modal-actions{display:flex;justify-content:flex-end;margin-top:22px}
.login-screen{position:fixed;inset:0;background:var(--bg);z-index:50;display:none;align-items:center;justify-content:center;padding:20px}
.login-screen.show{display:flex}
.login-card{background:white;border:1px solid var(--line);border-radius:9px;padding:35px;width:100%;max-width:390px}
.login-card h2{margin:18px 0 8px}
.login-card p{font-size:13px;color:var(--muted);line-height:1.6}
.login-card input{margin:15px 0 12px}
.dark{
  --bg:#10151e;--surface:#171f2b;--surface2:#1c2634;--text:#edf1f7;
  --muted:#a3adbd;--line:#303b4b;--blue:#7797ff;--blue-light:#253454;
  --shadow:none
}
.dark .topbar,.dark .field,.dark .option,.dark .small-btn,.dark .secondary-btn,.dark .save-btn,.dark .level-btn,.dark .nav-q{background:var(--surface)}
.dark .option-letter{background:#293444}
.dark .option.correct{background:#17382d}
.dark .option.incorrect{background:#3a2429}
.dark .answer-feedback.good{background:#17382d;color:#a8e4c7}
.dark .answer-feedback.bad{background:#3a2429;color:#ffc1c4}
.dark .modal,.dark .login-card{background:var(--surface)}
.dark .sidebar{background:var(--surface)}
@media(max-width:1050px){
  .bank-layout{grid-template-columns:minmax(0,1fr) 240px}
  .content{padding:25px}
  .section-grid{grid-template-columns:repeat(2,minmax(0,1fr))}
}
@media(max-width:760px){
  #app{grid-template-columns:72px minmax(0,1fr)}
  .sidebar{padding:18px 8px}
  .brand{padding:0 8px 25px}
  .brand-name,.nav-label,.nav-item span:not(.nav-icon),.user-details{display:none}
  .nav-item{justify-content:center;padding:12px 4px}
  .nav-icon{font-size:17px}
  .user-block{justify-content:center;padding:15px 0}
  .topbar{padding:0 16px}
  .content{padding:22px 15px 45px}
  .bank-layout{grid-template-columns:1fr}
  .side-stack{grid-template-columns:1fr 1fr}
  .stats{grid-template-columns:repeat(2,minmax(0,1fr))}
  .bank-toolbar{grid-template-columns:1fr}
  .topic-grid,.section-grid,.data-grid{grid-template-columns:1fr}
  h1{font-size:24px}
  .question-panel{padding:20px 17px}
  .question-text{font-size:15px}
}
@media(max-width:430px){
  .side-stack{grid-template-columns:1fr}
  .stats{gap:8px}
  .stat{padding:15px}
  .stat-value{font-size:22px}
}
</style>
</head>
<body>

<div id="app">
  <aside class="sidebar">
    <div class="brand">
      <div class="brand-mark">S</div>
      <div class="brand-name">SATboost</div>
    </div>

    <div class="nav-label">STUDY</div>
    <button class="nav-item active" data-page="dashboard"><span class="nav-icon">▦</span><span>Dashboard</span></button>
    <button class="nav-item" data-page="bank"><span class="nav-icon">▤</span><span>Question Bank</span></button>

    <div class="nav-label">SUBJECTS</div>
    <button class="nav-item" data-subject="Math"><span class="nav-icon">∑</span><span>Math</span></button>
    <button class="nav-item" data-subject="Reading"><span class="nav-icon">▤</span><span>Reading</span></button>
    <button class="nav-item" data-subject="Writing"><span class="nav-icon">✎</span><span>Writing</span></button>

    <div class="nav-label">YOUR PROGRESS</div>
    <button class="nav-item" data-page="mistakes"><span class="nav-icon">↻</span><span>My Mistakes</span></button>
    <button class="nav-item" data-page="saved"><span class="nav-icon">☆</span><span>Saved Questions</span></button>
    <button class="nav-item" data-page="data"><span class="nav-icon">▥</span><span>My Data</span></button>
    <button class="nav-item" data-page="materials"><span class="nav-icon">▧</span><span>Study Materials</span></button>

    <div class="sidebar-bottom">
      <div class="nav-divider"></div>
      <button class="nav-item" id="themeBtn"><span class="nav-icon">◐</span><span>Toggle theme</span></button>
      <button class="nav-item" id="logoutBtn"><span class="nav-icon">⇥</span><span>Log out</span></button>
      <div class="user-block">
        <div class="avatar">S</div>
        <div class="user-details">
          <div class="user-email" id="userEmail">Student</div>
          <div class="user-role">SATboost student</div>
        </div>
      </div>
    </div>
  </aside>

  <main class="main">
    <header class="topbar">
      <div class="breadcrumb" id="breadcrumb">SATboost / Dashboard</div>
      <div class="top-actions">
        <button class="small-btn" id="fontDown">A−</button>
        <button class="small-btn" id="fontUp">A+</button>
      </div>
    </header>
    <div class="content" id="content"></div>
  </main>
</div>

<div class="modal-backdrop" id="modalBackdrop">
  <div class="modal">
    <h2 id="modalTitle">Coming soon</h2>
    <p id="modalText">This section is currently being prepared.</p>
    <div class="modal-actions"><button class="primary-btn" id="modalClose">Close</button></div>
  </div>
</div>

<div class="login-screen" id="loginScreen">
  <div class="login-card">
    <div class="brand" style="padding:0">
      <div class="brand-mark">S</div><div class="brand-name">SATboost</div>
    </div>
    <h2>Welcome back</h2>
    <p>Sign in to access your SAT preparation workspace.</p>
    <input class="field" id="loginEmail" type="email" placeholder="Enter your email">
    <button class="primary-btn" id="loginBtn" style="width:100%">Continue</button>
    <p style="font-size:11px;margin-top:14px">This prototype stores your session in this browser.</p>
  </div>
</div>

<script>
/* -------------------------------------------------------
   QUESTION BANK
   These are original demonstration questions.
   Add your authorized questions to this data structure.
------------------------------------------------------- */

const topics = [
  {id:"boundaries",name:"Boundaries",description:"Punctuation, sentence boundaries, and relationships between clauses."},
  {id:"form",name:"Form, Structure & Sense",description:"Grammar, agreement, verb forms, and logical sentence construction."},
  {id:"transitions",name:"Transitions",description:"Choose transitions that establish the correct logical relationship."},
  {id:"rhetorical",name:"Rhetorical Synthesis",description:"Use notes and goals to select the most effective sentence."}
];

const questionBank = {
  boundaries:{
    Medium:[
      {
        text:"The research team collected data from several coastal regions ____ the results revealed a clear pattern in water temperature.",
        options:["regions, and the","regions; the","regions the","regions, the"],
        answer:1,
        explanation:"The sentence contains two independent clauses. A semicolon can correctly join two closely related independent clauses.",
        further:"A comma alone cannot join two independent clauses. This error is called a comma splice. The semicolon is appropriate because both sides can stand as complete sentences."
      },
      {
        text:"The museum's newest exhibition features paintings from several centuries ____ it also includes a collection of historical photographs.",
        options:["centuries,","centuries;","centuries because","centuries which"],
        answer:1,
        explanation:"Both parts are independent clauses, so a semicolon correctly connects them.",
        further:"The words before and after the blank each form a complete sentence. A semicolon can connect them without adding a coordinating conjunction."
      }
    ],
    Hard:[
      {
        text:"Although the initial results were promising ____ the researchers decided to repeat the experiment before publishing their findings.",
        options:["promising,","promising;","promising","promising:"],
        answer:0,
        explanation:"The dependent clause beginning with 'Although' must be followed by a comma before the independent clause.",
        further:"An introductory dependent clause is commonly separated from the main clause by a comma. A semicolon cannot separate a dependent clause from its main clause."
      },
      {
        text:"The architect revised the original design several times ____ the final structure retained the building's distinctive shape.",
        options:["times, however,","times; however,","times however","times: however,"],
        answer:1,
        explanation:"A semicolon before the conjunctive adverb 'however' and a comma after it correctly connect the clauses.",
        further:"When 'however' connects two independent clauses, use a semicolon before it and a comma after it. The clauses on both sides must be complete sentences."
      }
    ]
  },
  form:{
    Medium:[
      {
        text:"The collection of ancient maps ____ on display in the university library this month.",
        options:["are","were","is","have been"],
        answer:2,
        explanation:"The subject is 'collection,' which is singular. Therefore, the singular verb 'is' is correct.",
        further:"Do not let the plural noun 'maps' distract you. The subject of the sentence is the singular collective noun 'collection.'"
      },
      {
        text:"By the time the lecture began, most students ____ their seats.",
        options:["take","had taken","are taking","will take"],
        answer:1,
        explanation:"The past perfect 'had taken' indicates an action completed before another past event.",
        further:"The lecture beginning is the later past event. The students taking their seats happened before it, so past perfect is appropriate."
      }
    ],
    Hard:[
      {
        text:"Neither the revised proposal nor the earlier recommendations ____ sufficient evidence to support the conclusion.",
        options:["provides","provide","has provided","is providing"],
        answer:1,
        explanation:"With 'neither...nor,' the verb agrees with the nearer subject. 'Recommendations' is plural, so 'provide' is correct.",
        further:"In this construction, the verb generally agrees with the subject closest to it. The nearest subject is 'recommendations,' a plural noun."
      },
      {
        text:"The scientist, along with two research assistants, ____ the results of the experiment every Friday.",
        options:["review","are reviewing","reviews","have reviewed"],
        answer:2,
        explanation:"The main subject is the singular noun 'scientist.' The phrase between commas does not change subject-verb agreement.",
        further:"Phrases such as 'along with,' 'as well as,' and 'together with' do not make a singular subject plural. The correct verb is 'reviews.'"
      }
    ]
  },
  transitions:{
    Medium:[
      {
        text:"Several studies have examined the effects of urban green spaces on air quality. ____, recent research has also explored their influence on residents' mental well-being.",
        options:["In contrast","Furthermore","Nevertheless","Instead"],
        answer:1,
        explanation:"'Furthermore' adds another related point to the information in the previous sentence.",
        further:"The second sentence introduces an additional area of research, not a contrast or contradiction. An additive transition is the best choice."
      },
      {
        text:"The first version of the software contained several errors. ____, the development team released an updated version after extensive testing.",
        options:["For example","As a result","Similarly","In comparison"],
        answer:1,
        explanation:"'As a result' signals that the second event follows from the situation described in the first sentence.",
        further:"The updated release is a consequence of the problems with the earlier version. A cause-and-effect transition communicates that relationship."
      }
    ],
    Hard:[
      {
        text:"The ancient settlement was once believed to have been abandoned suddenly. ____, recent archaeological evidence suggests that its residents left gradually over several decades.",
        options:["Consequently","In other words","However","For instance"],
        answer:2,
        explanation:"'However' signals a contrast between the earlier belief and the newer evidence.",
        further:"The two sentences present conflicting interpretations. The second sentence challenges the first, so a contrast transition is needed."
      },
      {
        text:"The study's sample size was relatively small. ____, its findings provide a useful starting point for future research.",
        options:["Nevertheless","For example","Likewise","In addition to"],
        answer:0,
        explanation:"'Nevertheless' introduces a statement that contrasts with an expected conclusion.",
        further:"A small sample size is a limitation, but the findings are still useful. 'Nevertheless' expresses this concession."
      }
    ]
  },
  rhetorical:{
    Medium:[
      {
        text:"A student is writing about a museum exhibition. The student wants to emphasize that the exhibition includes works from different historical periods.\n\nNotes:\n• The exhibition opened in 2024.\n• It contains 60 paintings.\n• The paintings were created between 1600 and 1950.\n• The exhibition is located in the city art museum.\n\nWhich choice most effectively uses relevant information from the notes to accomplish the student's goal?",
        options:[
          "The city art museum opened its exhibition in 2024.",
          "The exhibition features 60 paintings created between 1600 and 1950.",
          "The exhibition is located in a museum in the city.",
          "The museum contains many works of art."
        ],
        answer:1,
        explanation:"Choice B directly emphasizes the range of historical periods represented by the paintings.",
        further:"The goal is to highlight different historical periods. The dates 1600 and 1950 clearly demonstrate that range. The other choices focus on location, opening date, or general information."
      },
      {
        text:"A student is writing about a scientific research project. The student wants to emphasize the project's international collaboration.\n\nNotes:\n• The project began in 2022.\n• Researchers from five countries participated.\n• The team studied ocean temperatures.\n• The results were published in 2025.\n\nWhich choice best emphasizes international collaboration?",
        options:[
          "The research project began in 2022.",
          "The team's findings were published in 2025.",
          "Researchers from five countries worked together on the project.",
          "The project examined changes in ocean temperatures."
        ],
        answer:2,
        explanation:"Choice C directly states that researchers from five countries collaborated.",
        further:"The question asks specifically about international collaboration. The number of participating countries and the phrase 'worked together' communicate that idea most clearly."
      }
    ],
    Hard:[
      {
        text:"A student is writing about an architectural design. The student wants to emphasize how the design reduces energy consumption.\n\nNotes:\n• The building opened in 2023.\n• Its windows allow natural light into the offices.\n• Solar panels cover part of the roof.\n• The building has 12 floors.\n\nWhich choice most effectively achieves the student's goal?",
        options:[
          "The twelve-story building opened in 2023.",
          "The building uses natural lighting and rooftop solar panels to reduce its reliance on external energy sources.",
          "The building has offices on twelve different floors.",
          "Solar panels have become increasingly common in modern architecture."
        ],
        answer:1,
        explanation:"Choice B combines two relevant design features and connects them directly to reduced energy consumption.",
        further:"The goal is not simply to describe the building. It is to explain how its features reduce energy use. Natural lighting and solar panels are both relevant pieces of evidence."
      },
      {
        text:"A student is writing about a conservation program. The student wants to emphasize the program's measurable impact on local wildlife.\n\nNotes:\n• The program began in 2019.\n• It restored 40 hectares of wetland.\n• The population of a local bird species increased by 25% over four years.\n• Volunteers organized monthly events.\n\nWhich choice best achieves the student's goal?",
        options:[
          "The conservation program began in 2019.",
          "Volunteers organized monthly events to support the conservation program.",
          "After the program restored 40 hectares of wetland, the local bird population increased by 25% over four years.",
          "Wetlands provide habitats for many species of birds."
        ],
        answer:2,
        explanation:"Choice C connects a specific conservation action with a measurable change in the wildlife population.",
        further:"The goal is to show measurable impact. The 25% increase is quantitative evidence, and the restored wetland provides relevant context. The other options do not demonstrate the outcome."
      }
    ]
  }
};

/* -------------------------------------------------------
   APP STATE
------------------------------------------------------- */

let currentPage = "dashboard";
let currentTopic = "boundaries";
let currentLevel = "Medium";
let currentIndex = 0;
let selectedAnswer = null;
let checked = false;
let fontSize = 17;

let stats = JSON.parse(localStorage.getItem("satboost_stats") || '{"answered":0,"correct":0}');
let saved = JSON.parse(localStorage.getItem("satboost_saved") || "[]");
let mistakes = JSON.parse(localStorage.getItem("satboost_mistakes") || "[]");
let completed = JSON.parse(localStorage.getItem("satboost_completed") || "[]");

const content = document.getElementById("content");

function saveData(){
  localStorage.setItem("satboost_stats",JSON.stringify(stats));
  localStorage.setItem("satboost_saved",JSON.stringify(saved));
  localStorage.setItem("satboost_mistakes",JSON.stringify(mistakes));
  localStorage.setItem("satboost_completed",JSON.stringify(completed));
}
function questions(){
  return questionBank[currentTopic]?.[currentLevel] || [];
}
function allQuestionsCount(){
  let n=0;
  Object.values(questionBank).forEach(topic=>{
    Object.values(topic).forEach(level=>n+=level.length);
  });
  return n;
}
function topicCount(id){
  return Object.values(questionBank[id]||{}).reduce((sum,arr)=>sum+arr.length,0);
}
function esc(s){
  return String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
}
function setPage(page){
  currentPage=page;
  document.querySelectorAll(".nav-item[data-page],.nav-item[data-subject]").forEach(b=>b.classList.remove("active"));
  const nav=document.querySelector(`[data-page="${page}"]`);
  if(nav)nav.classList.add("active");
  render();
}
function showModal(title,message){
  document.getElementById("modalTitle").textContent=title;
  document.getElementById("modalText").textContent=message;
  document.getElementById("modalBackdrop").classList.add("show");
}
function selectSubject(subject){
  if(subject!=="Writing"){
    showModal("Coming soon",subject+" question bank is currently being prepared. It will be available in a future update.");
    return;
  }
  setPage("bank");
  renderTopics();
}
function render(){
  const labels={
    dashboard:"Dashboard",bank:"Question Bank",mistakes:"My Mistakes",
    saved:"Saved Questions",data:"My Data",materials:"Study Materials"
  };
  document.getElementById("breadcrumb").textContent="SATboost / "+(labels[currentPage]||"Question Bank");
  if(currentPage==="dashboard")renderDashboard();
  if(currentPage==="bank")renderTopics();
  if(currentPage==="mistakes")renderMistakes();
  if(currentPage==="saved")renderSaved();
  if(currentPage==="data")renderData();
  if(currentPage==="materials")renderMaterials();
}

/* -------------------------------------------------------
   DASHBOARD
------------------------------------------------------- */

function renderDashboard(){
  const accuracy=stats.answered?Math.round(stats.correct/stats.answered*100)+"%":"—";
  content.innerHTML=`
    <div class="page-heading">
      <div><div class="eyebrow">YOUR STUDY SPACE</div><h1>Dashboard</h1></div>
    </div>
    <section class="panel welcome">
      <div class="eyebrow">WELCOME TO SATBOOST</div>
      <h2>Prepare smarter. Achieve more.</h2>
      <p>Your SAT preparation workspace. Practice by skill, review your mistakes, and follow your progress.</p>
      <button class="primary-btn" onclick="setPage('bank')">Open Question Bank →</button>
    </section>
    <div class="stats">
      <div class="panel stat"><div class="stat-label">Questions answered</div><div class="stat-value">${stats.answered}</div></div>
      <div class="panel stat"><div class="stat-label">Correct answers</div><div class="stat-value">${stats.correct}</div></div>
      <div class="panel stat"><div class="stat-label">Accuracy</div><div class="stat-value">${accuracy}</div></div>
      <div class="panel stat"><div class="stat-label">Saved questions</div><div class="stat-value">${saved.length}</div></div>
    </div>
    <div class="section-heading"><h2>Question Bank</h2><span class="subtitle">Choose a subject to begin</span></div>
    <div class="section-grid">
      <div class="panel subject-card" onclick="selectSubject('Math')">
        <div class="subject-icon">∑</div><h3>Math</h3>
        <p>Algebra, Advanced Math, Problem Solving and Geometry.</p>
        <span class="coming">COMING SOON</span>
      </div>
      <div class="panel subject-card" onclick="selectSubject('Reading')">
        <div class="subject-icon">▤</div><h3>Reading</h3>
        <p>Information and Ideas, Craft and Structure, and other reading skills.</p>
        <span class="coming">COMING SOON</span>
      </div>
      <div class="panel subject-card" onclick="selectSubject('Writing')">
        <div class="subject-icon">✎</div><h3>Writing</h3>
        <p>Four skills covering Standard English Conventions and Expression of Ideas.</p>
        <div class="card-foot">Explore Writing →</div>
      </div>
    </div>`;
}

/* -------------------------------------------------------
   WRITING TOPICS + LEVEL SELECTION
------------------------------------------------------- */

function renderTopics(){
  content.innerHTML=`
    <div class="page-heading">
      <div><div class="eyebrow">READING & WRITING</div><h1>Writing Question Bank</h1>
      <div class="subtitle">Select a skill, then choose your difficulty level.</div></div>
      <span class="tag">WRITING</span>
    </div>
    <div class="section-heading"><h2>Standard English Conventions</h2></div>
    <div class="topic-grid">
      ${topicCard(topics[0],1)}
      ${topicCard(topics[1],2)}
    </div>
    <div class="section-heading"><h2>Expression of Ideas</h2></div>
    <div class="topic-grid">
      ${topicCard(topics[2],3)}
      ${topicCard(topics[3],4)}
    </div>
    <div class="subtitle" style="margin-top:24px">Demonstration questions currently loaded: ${allQuestionsCount()}. Additional question sets can be added to each skill and difficulty level.</div>`;
}
function topicCard(topic,num){
  return `<div class="panel topic-card">
    <div class="topic-top"><span class="topic-number">SKILL 0${num}</span><span class="topic-count">${topicCount(topic.id)} questions loaded</span></div>
    <h3>${topic.name}</h3>
    <p>${topic.description}</p>
    <div class="level-row">
      <button class="level-btn" onclick="openTopic('${topic.id}','Medium')">Medium</button>
      <button class="level-btn" onclick="openTopic('${topic.id}','Hard')">Hard</button>
    </div>
  </div>`;
}
function openTopic(topic,level){
  currentTopic=topic;
  currentLevel=level;
  currentIndex=0;
  selectedAnswer=null;
  checked=false;
  currentPage="bank";
  document.querySelectorAll(".nav-item").forEach(b=>b.classList.remove("active"));
  document.querySelector('[data-page="bank"]').classList.add("active");
  renderQuestion();
}

/* -------------------------------------------------------
   QUESTION VIEW
------------------------------------------------------- */

function renderQuestion(){
  const list=questions();
  if(!list.length){
    content.innerHTML=`<div class="page-heading"><div><div class="eyebrow">QUESTION BANK</div><h1>${topicName()}</h1></div></div>
      <div class="panel empty-state"><h3>No questions available yet</h3>This question set is ready for content. Questions will appear here once added.<br><br><button class="secondary-btn" onclick="renderTopics()">Back to all skills</button></div>`;
    return;
  }
  if(currentIndex>=list.length)currentIndex=list.length-1;
  const q=list[currentIndex];
  const topic=topicName();
  const key=questionKey(q);
  const isSaved=saved.includes(key);
  const progress=completed.filter(x=>x.startsWith(currentTopic+"-"+currentLevel+"-")).length;
  const pct=Math.round(progress/list.length*100);

  content.innerHTML=`
    <div class="page-heading">
      <div>
        <div class="eyebrow">READING & WRITING / ${esc(topic.toUpperCase())}</div>
        <h1>${esc(topic)}</h1>
        <div class="subtitle">${currentLevel} practice · ${list.length} questions in this set</div>
      </div>
      <button class="secondary-btn" onclick="renderTopics()">← All skills</button>
    </div>
    <div class="bank-toolbar">
      <input class="field" id="searchQuestion" placeholder="Search within this skill..." oninput="searchCurrentQuestion(this.value)">
      <select class="field" onchange="changeLevel(this.value)">
        <option ${currentLevel==="Medium"?"selected":""}>Medium</option>
        <option ${currentLevel==="Hard"?"selected":""}>Hard</option>
      </select>
      <select class="field" onchange="changeTopic(this.value)">
        ${topics.map(t=>`<option value="${t.id}" ${t.id===currentTopic?"selected":""}>${t.name}</option>`).join("")}
      </select>
    </div>
    <div class="bank-layout">
      <section class="panel question-panel">
        <div class="question-meta">
          <div><span class="tag">${esc(topic)}</span><span class="difficulty">${currentLevel}</span></div>
          <button class="save-btn" onclick="toggleSave('${key}')">${isSaved?"★ Saved":"☆ Save question"}</button>
        </div>
        <div class="question-number">QUESTION ${currentIndex+1} OF ${list.length}</div>
        <p class="question-text" style="font-size:${fontSize}px">${esc(q.text)}</p>
        <div class="options">
          ${q.options.map((option,i)=>{
            let cls="";
            if(checked&&i===q.answer)cls="correct";
            else if(checked&&i===selectedAnswer&&i!==q.answer)cls="incorrect";
            return `<button class="option ${cls}" ${checked?"disabled":""} onclick="selectOption(${i})">
              <span class="option-letter">${"ABCD"[i]}</span><span>${esc(option)}</span>
            </button>`;
          }).join("")}
        </div>
        <div class="answer-feedback ${checked?"show "+(selectedAnswer===q.answer?"good":"bad"):""}" id="feedback">
          <strong>${checked?(selectedAnswer===q.answer?"Correct answer":"Not quite"):""}</strong>
          ${checked?`<div class="explanation"><strong>Explanation:</strong><br>${esc(q.explanation)}
          <div style="margin-top:12px"><button class="secondary-btn" onclick="toggleFurther()">Further explanation</button></div>
          <div class="further" id="further"><strong>Further explanation:</strong><br>${esc(q.further)}</div></div>`:""}
        </div>
        <div class="question-actions">
          ${!checked?`<button class="primary-btn" onclick="checkAnswer()" ${selectedAnswer===null?"disabled":""}>Check answer</button>`:
          `<button class="primary-btn" onclick="nextQuestion()">Next question →</button>`}
          <button class="secondary-btn" onclick="renderTopics()">Back to skills</button>
        </div>
      </section>
      <aside class="side-stack">
        <div class="panel side-panel">
          <h3>Question progress</h3>
          <div class="progress-number">${progress}/${list.length}</div>
          <div class="progress-track"><div class="progress-fill" style="width:${pct}%"></div></div>
          <div class="muted-small">Questions answered in this practice set.</div>
        </div>
        <div class="panel side-panel">
          <h3>Question navigator</h3>
          <div class="navigator">
            ${list.map((item,i)=>{
              const done=completed.includes(currentTopic+"-"+currentLevel+"-"+i);
              return `<button class="nav-q ${i===currentIndex?"current":""} ${done?"done":""}" onclick="goQuestion(${i})">${i+1}</button>`;
            }).join("")}
          </div>
          <div class="muted-small">Select a question to navigate.</div>
        </div>
        <div class="panel side-panel">
          <h3>Study tip</h3>
          <div class="muted-small">Read the complete sentence or passage before choosing an answer. After checking your answer, review the explanation to understand the reasoning.</div>
        </div>
      </aside>
    </div>`;
}
function topicName(){
  return topics.find(t=>t.id===currentTopic)?.name||"Writing";
}
function questionKey(q){
  return currentTopic+"-"+currentLevel+"-"+currentIndex;
}
function selectOption(i){
  if(checked)return;
  selectedAnswer=i;
  renderQuestion();
}
function checkAnswer(){
  if(selectedAnswer===null||checked)return;
  checked=true;
  const q=questions()[currentIndex];
  stats.answered++;
  if(selectedAnswer===q.answer)stats.correct++;
  else if(!mistakes.includes(questionKey(q)))mistakes.push(questionKey(q));
  const id=currentTopic+"-"+currentLevel+"-"+currentIndex;
  if(!completed.includes(id))completed.push(id);
  saveData();
  renderQuestion();
}
function nextQuestion(){
  if(currentIndex<questions().length-1)currentIndex++;
  else{
    showModal("Practice set completed","You have reached the end of this practice set. You can return to the skill list and choose another level.");
    return;
  }
  selectedAnswer=null;
  checked=false;
  renderQuestion();
}
function goQuestion(i){
  currentIndex=i;selectedAnswer=null;checked=false;renderQuestion();
}
function toggleFurther(){
  const el=document.getElementById("further");
  if(el)el.classList.toggle("show");
}
function toggleSave(key){
  if(saved.includes(key))saved=saved.filter(x=>x!==key);
  else saved.push(key);
  saveData();renderQuestion();
}
function changeLevel(level){
  currentLevel=level;currentIndex=0;selectedAnswer=null;checked=false;renderQuestion();
}
function changeTopic(topic){
  currentTopic=topic;currentIndex=0;selectedAnswer=null;checked=false;renderQuestion();
}
function searchCurrentQuestion(value){
  const list=questions();
  const found=list.findIndex(q=>q.text.toLowerCase().includes(value.toLowerCase()));
  if(value.trim()&&found>=0){currentIndex=found;selectedAnswer=null;checked=false;renderQuestion();}
}

/* -------------------------------------------------------
   SAVED / MISTAKES / DATA / MATERIALS
------------------------------------------------------- */

function findQuestionByKey(key){
  const [topic,level,index]=key.split("-");
  const q=questionBank[topic]?.[level]?.[Number(index)];
  if(!q)return null;
  return {q,topic,level,index:Number(index)};
}
function renderSaved(){
  const items=saved.map(findQuestionByKey).filter(Boolean);
  content.innerHTML=`<div class="page-heading"><div><div class="eyebrow">YOUR PROGRESS</div><h1>Saved Questions</h1><div class="subtitle">Questions you have bookmarked for later review.</div></div></div>
  <div class="panel" style="padding:22px">
  ${items.length?items.map(x=>`<div class="list-row"><div><strong>${esc(topics.find(t=>t.id===x.topic)?.name||x.topic)}</strong><div class="muted-small">${esc(x.q.text.slice(0,115))}...</div></div><button class="secondary-btn" onclick="openSaved('${x.topic}','${x.level}',${x.index})">Open</button></div>`).join(""):`<div class="empty-state"><h3>No saved questions</h3>Use the Save question button in the Question Bank to bookmark questions.</div>`}
  </div>`;
}
function openSaved(topic,level,index){
  currentTopic=topic;currentLevel=level;currentIndex=index;selectedAnswer=null;checked=false;currentPage="bank";renderQuestion();
}
function renderMistakes(){
  const items=mistakes.map(findQuestionByKey).filter(Boolean);
  content.innerHTML=`<div class="page-heading"><div><div class="eyebrow">YOUR PROGRESS</div><h1>My Mistakes</h1><div class="subtitle">Review questions you answered incorrectly.</div></div></div>
  <div class="panel" style="padding:22px">
  ${items.length?items.map(x=>`<div class="list-row"><div><strong>${esc(topics.find(t=>t.id===x.topic)?.name||x.topic)}</strong><div class="muted-small">${esc(x.q.text.slice(0,115))}...</div></div><button class="secondary-btn" onclick="openSaved('${x.topic}','${x.level}',${x.index})">Review</button></div>`).join(""):`<div class="empty-state"><h3>No mistakes recorded</h3>Questions you answer incorrectly will appear here.</div>`}
  </div>`;
}
function renderData(){
  const accuracy=stats.answered?Math.round(stats.correct/stats.answered*100)+"%":"—";
  content.innerHTML=`<div class="page-heading"><div><div class="eyebrow">YOUR PROGRESS</div><h1>My Data</h1><div class="subtitle">Your practice statistics.</div></div></div>
  <div class="stats">
    <div class="panel stat"><div class="stat-label">Questions answered</div><div class="stat-value">${stats.answered}</div></div>
    <div class="panel stat"><div class="stat-label">Correct answers</div><div class="stat-value">${stats.correct}</div></div>
    <div class="panel stat"><div class="stat-label">Accuracy</div><div class="stat-value">${accuracy}</div></div>
    <div class="panel stat"><div class="stat-label">Saved questions</div><div class="stat-value">${saved.length}</div></div>
  </div>
  <div class="panel data-card"><h3>About your data</h3><p>Your practice statistics are stored in this browser. They are not synced across devices in this prototype.</p></div>`;
}
function renderMaterials(){
  content.innerHTML=`<div class="page-heading"><div><div class="eyebrow">RESOURCES</div><h1>Study Materials</h1><div class="subtitle">Useful resources for your SAT preparation.</div></div></div>
  <div class="section-grid">
    <div class="panel subject-card"><h3>Official SAT Practice</h3><p>Access official SAT preparation resources.</p><a href="https://satsuite.collegeboard.org/sat/practice-preparation" target="_blank">College Board resources ↗</a></div>
    <div class="panel subject-card"><h3>Bluebook</h3><p>Learn about the digital testing application.</p><a href="https://bluebook.collegeboard.org/" target="_blank">Open Bluebook ↗</a></div>
  </div>`;
}

/* -------------------------------------------------------
   NAVIGATION AND SETTINGS
------------------------------------------------------- */

document.querySelectorAll("[data-page]").forEach(btn=>{
  btn.addEventListener("click",()=>setPage(btn.dataset.page));
});
document.querySelectorAll("[data-subject]").forEach(btn=>{
  btn.addEventListener("click",()=>selectSubject(btn.dataset.subject));
});
document.getElementById("themeBtn").addEventListener("click",()=>{
  document.body.classList.toggle("dark");
  localStorage.setItem("satboost_theme",document.body.classList.contains("dark")?"dark":"light");
});
document.getElementById("fontDown").addEventListener("click",()=>{
  fontSize=Math.max(14,fontSize-1);
  if(currentPage==="bank")renderQuestion();
});
document.getElementById("fontUp").addEventListener("click",()=>{
  fontSize=Math.min(23,fontSize+1);
  if(currentPage==="bank")renderQuestion();
});
document.getElementById("modalClose").addEventListener("click",()=>{
  document.getElementById("modalBackdrop").classList.remove("show");
});
document.getElementById("modalBackdrop").addEventListener("click",e=>{
  if(e.target.id==="modalBackdrop")e.currentTarget.classList.remove("show");
});

/* -------------------------------------------------------
   SIMPLE EMAIL SESSION
------------------------------------------------------- */

function showLogin(){
  document.getElementById("loginScreen").classList.add("show");
}
function hideLogin(email){
  document.getElementById("loginScreen").classList.remove("show");
  document.getElementById("userEmail").textContent=email;
  localStorage.setItem("satboost_email",email);
}
document.getElementById("loginBtn").addEventListener("click",()=>{
  const email=document.getElementById("loginEmail").value.trim();
  if(!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)){
    alert("Please enter a valid email address.");
    return;
  }
  hideLogin(email);
});
document.getElementById("logoutBtn").addEventListener("click",()=>{
  localStorage.removeItem("satboost_email");
  showLogin();
});
const storedEmail=localStorage.getItem("satboost_email");
if(storedEmail){
  document.getElementById("userEmail").textContent=storedEmail;
}else{
  showLogin();
}
if(localStorage.getItem("satboost_theme")==="dark")document.body.classList.add("dark");

render();
</script>
</body>
</html>
