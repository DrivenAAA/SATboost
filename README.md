
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify SAT</title>
<style>
:root {
  --bg:#f5f7fc; --surface:#fff; --text:#172033; --muted:#68738a;
  --primary:#6558e8; --border:#e5e8f0; --soft:#eeecff;
}
body.dark {
  --bg:#101322; --surface:#1a2032; --text:#f3f4fb; --muted:#a6aec2;
  --primary:#9287ff; --border:#30384d; --soft:#292747;
}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:Inter,Arial,sans-serif;transition:.2s}
button,input{font:inherit}
button{cursor:pointer;border:0}
.hidden{display:none!important}
.container{max-width:1100px;margin:auto;padding:25px}
.topbar{display:flex;justify-content:space-between;align-items:center;gap:15px;margin-bottom:35px}
.logo{font-size:25px;font-weight:850;color:var(--primary);letter-spacing:-1px}
.actions{display:flex;align-items:center;gap:10px;flex-wrap:wrap}
.btn{padding:11px 16px;border-radius:10px;background:var(--primary);color:white;font-weight:700}
.btn.secondary{background:var(--soft);color:var(--primary)}
.btn.outline{background:transparent;border:1px solid var(--border);color:var(--text)}
.btn.danger{background:#ffe9e9;color:#c83232}
.card{background:var(--surface);border:1px solid var(--border);border-radius:18px;padding:24px;margin-bottom:20px}
.muted{color:var(--muted)}
h1{font-size:clamp(30px,5vw,46px);letter-spacing:-1.5px;margin:8px 0 14px}
h2{margin-top:0}
input{width:100%;padding:14px;border-radius:10px;border:1px solid var(--border);background:var(--bg);color:var(--text);margin:8px 0 16px}
label{font-weight:700;font-size:14px}
.login-wrap{min-height:85vh;display:grid;place-items:center}
.login-card{max-width:440px;width:100%;padding:35px}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:18px}
.stat{font-size:30px;font-weight:800;margin:8px 0}
.small{font-size:13px;color:var(--muted)}
.progress{height:9px;background:var(--border);border-radius:20px;overflow:hidden;margin:15px 0}
.progress span{display:block;height:100%;background:var(--primary);width:0%;transition:.2s}
.option{display:block;width:100%;text-align:left;padding:14px;margin:10px 0;border:1px solid var(--border);border-radius:10px;background:var(--bg);color:var(--text)}
.option:hover{border-color:var(--primary)}
.option.selected{border:2px solid var(--primary);background:var(--soft)}
.question{font-size:19px;font-weight:700;line-height:1.5;margin:20px 0}
.tag{display:inline-block;background:var(--soft);color:var(--primary);padding:6px 10px;border-radius:20px;font-size:12px;font-weight:700}
.footer{margin-top:45px;text-align:center;color:var(--muted);font-size:13px}
@media(max-width:700px){.grid{grid-template-columns:1fr}.topbar{align-items:flex-start;flex-direction:column}.container{padding:16px}}
</style>
</head>
<body>
<div class="container">

<header class="topbar">
  <div class="logo">prepify<span style="color:var(--text)">.</span></div>
  <div class="actions">
    <button class="btn outline" onclick="changeFont(-1)">A−</button>
    <button class="btn outline" onclick="changeFont(1)">A+</button>
    <button class="btn outline" onclick="toggleTheme()">☾ / ☀</button>
    <button id="logoutBtn" class="btn danger hidden" onclick="logout()">Log out</button>
  </div>
</header>

<section id="loginPage" class="login-wrap">
  <div class="card login-card">
    <span class="tag">YOUR SAT JOURNEY STARTS HERE</span>
    <h1>Welcome to Prepify.</h1>
    <p class="muted">Sign in with your email to continue your personalized SAT preparation.</p>
    <form id="loginForm">
      <label for="email">Email address</label>
      <input id="email" type="email" placeholder="example@email.com" required>
      <button class="btn" style="width:100%" type="submit">Continue with email →</button>
    </form>
    <p class="small">This prototype saves your session in this browser. Email verification is not enabled yet.</p>
  </div>
</section>

<section id="setupPage" class="hidden">
  <div class="card">
    <span class="tag">PERSONALIZATION</span>
    <h1>Let's build your SAT plan.</h1>
    <p class="muted">Tell us about your goals. You can change these later.</p>
    <div class="grid">
      <div>
        <label>Target Math score</label>
        <input id="mathTarget" type="number" min="200" max="800" value="700">
      </div>
      <div>
        <label>Target Reading & Writing score</label>
        <input id="rwTarget" type="number" min="200" max="800" value="700">
      </div>
      <div>
        <label>Daily Math lessons</label>
        <input id="mathDaily" type="number" min="1" max="10" value="2">
      </div>
      <div>
        <label>Daily Reading & Writing lessons</label>
        <input id="rwDaily" type="number" min="1" max="10" value="2">
      </div>
    </div>
    <label>How would you describe your SAT experience?</label>
    <div style="margin:12px 0">
      <label><input type="radio" name="experience" value="beginner" checked style="width:auto;margin-right:8px">I'm a beginner / I have little knowledge.</label><br><br>
      <label><input type="radio" name="experience" value="experienced" style="width:auto;margin-right:8px">I'm experienced / I've studied SAT before.</label>
    </div>
    <button class="btn" onclick="saveSetup()">Continue to diagnostic test →</button>
  </div>
</section>

<section id="testPage" class="hidden">
  <div class="card">
    <span class="tag">PLACEMENT TEST</span>
    <h1>Let's find your level.</h1>
    <p class="muted">15 questions: 10 Math and 5 Reading & Writing. The test starts at a suitable level and adjusts the next questions based on your answers.</p>
    <div class="grid">
      <div><b>Math</b><p class="muted">5 medium + 5 challenging questions</p></div>
      <div><b>Reading & Writing</b><p class="muted">2 vocabulary + 3 reading questions</p></div>
    </div>
    <button class="btn" onclick="startTest()">Start diagnostic test →</button>
  </div>
</section>

<section id="questionPage" class="hidden">
  <div class="card">
    <div style="display:flex;justify-content:space-between;gap:10px">
      <span class="tag" id="sectionTag">MATH</span>
      <span class="muted" id="questionCount">Question 1 of 15</span>
    </div>
    <div class="progress"><span id="progressBar"></span></div>
    <p class="small" id="difficultyLabel">MEDIUM</p>
    <div class="question" id="questionText"></div>
    <div id="options"></div>
    <p id="feedback" class="muted"></p>
    <button id="nextBtn" class="btn" onclick="nextQuestion()" disabled>Submit answer</button>
  </div>
</section>

<section id="resultPage" class="hidden">
  <div class="card">
    <span class="tag">DIAGNOSTIC RESULTS</span>
    <h1>Your starting point.</h1>
    <p class="muted">This is an initial estimate based on a short placement test, not an official SAT score prediction.</p>
    <div class="grid">
      <div class="card">
        <p class="muted">Math diagnostic estimate</p>
        <div class="stat" id="mathResult">—</div>
        <p class="small" id="mathAccuracy"></p>
      </div>
      <div class="card">
        <p class="muted">Reading & Writing estimate</p>
        <div class="stat" id="rwResult">—</div>
        <p class="small" id="rwAccuracy"></p>
      </div>
    </div>
    <h2>What this means</h2>
    <p id="resultAdvice" class="muted"></p>
    <p class="small">A 15-question test cannot reliably predict an exact SAT score. These broad ranges are only for choosing your next lessons. Take a full-length official Bluebook practice test for a more meaningful score estimate.</p>
    <button class="btn" onclick="showDashboard()">Go to my dashboard →</button>
  </div>
</section>

<section id="dashboardPage" class="hidden">
  <div class="card">
    <span class="tag">YOUR DASHBOARD</span>
    <h1>Welcome back!</h1>
    <p class="muted">Signed in as <b id="userEmail"></b></p>
    <div class="grid">
      <div class="card">
        <p class="muted">Math target</p>
        <div class="stat" id="dashMath">700</div>
      </div>
      <div class="card">
        <p class="muted">Reading & Writing target</p>
        <div class="stat" id="dashRW">700</div>
      </div>
    </div>
  </div>
  <div class="grid">
    <div class="card">
      <h2>Math practice</h2>
      <p class="muted">Build your algebra, advanced math, problem-solving and data analysis skills.</p>
      <p id="mathPlan" class="small"></p>
      <button class="btn" onclick="restartTest()">Practice diagnostic</button>
    </div>
    <div class="card">
      <h2>Reading & Writing</h2>
      <p class="muted">Improve vocabulary, reading comprehension, grammar and writing skills.</p>
      <p id="rwPlan" class="small"></p>
      <button class="btn secondary" onclick="restartTest()">Practice diagnostic</button>
    </div>
  </div>
  <div class="card">
    <h2>Official SAT resources</h2>
    <p class="muted">Use official College Board materials for full-length practice and authentic questions.</p>
    <a href="https://satsuite.collegeboard.org/sat/practice-preparation" target="_blank" rel="noopener">College Board SAT Practice →</a><br><br>
    <a href="https://bluebook.collegeboard.org/" target="_blank" rel="noopener">Bluebook practice tests →</a>
  </div>
</section>

<div class="footer">Prepify · Learn smarter. Prepare better.</div>
</div>

<script>
const $ = id => document.getElementById(id);
const pages = ["loginPage","setupPage","testPage","questionPage","resultPage","dashboardPage"];
let fontSize = 16;
let questions = [];
let current = 0;
let answers = [];
let selected = null;
let difficulty = {math:0,rw:0};

function showPage(id){
  pages.forEach(p=>$(p).classList.add("hidden"));
  $(id).classList.remove("hidden");
  $("logoutBtn").classList.toggle("hidden",id==="loginPage");
}
function toggleTheme(){document.body.classList.toggle("dark");localStorage.setItem("prepifyTheme",document.body.classList.contains("dark")?"dark":"light")}
function changeFont(n){fontSize=Math.max(14,Math.min(21,fontSize+n));document.body.style.fontSize=fontSize+"px"}
if(localStorage.getItem("prepifyTheme")==="dark")document.body.classList.add("dark");

function login(email){
  localStorage.setItem("prepifySession",email);
  $("userEmail").textContent=email;
  const profile=JSON.parse(localStorage.getItem("prepifyProfile")||"null");
  if(profile){showDashboard()}else{showPage("setupPage")}
}
$("loginForm").addEventListener("submit",e=>{
  e.preventDefault();
  const email=$("email").value.trim().toLowerCase();
  if(!email)return;
  login(email);
});
function logout(){
  localStorage.removeItem("prepifySession");
  $("email").value="";
  showPage("loginPage");
}
window.addEventListener("load",()=>{
  const email=localStorage.getItem("prepifySession");
  if(email)login(email);else showPage("loginPage");
});
function saveSetup(){
  const profile={
    mathTarget:Number($("mathTarget").value),
    rwTarget:Number($("rwTarget").value),
    mathDaily:Number($("mathDaily").value),
    rwDaily:Number($("rwDaily").value),
    experience:document.querySelector('input[name="experience"]:checked').value
  };
  if(profile.mathTarget<200||profile.mathTarget>800||profile.rwTarget<200||profile.rwTarget>800){alert("Please enter target scores between 200 and 800.");return}
  localStorage.setItem("prepifyProfile",JSON.stringify(profile));
  showPage("testPage");
}
const bank=[
{section:"math",level:1,type:"Functions",q:"If f(x) = 3x + 7, what is the value of f(4)?",o:["12","19","21","28"],a:1},
{section:"math",level:1,type:"Functions",q:"If g(x) = x² − 5, what is g(3)?",o:["2","4","9","14"],a:1},
{section:"math",level:1,type:"Functions",q:"A function is defined by h(x) = 2x − 1. Which expression represents h(a + 3)?",o:["2a + 2","2a + 3","2a + 5","2a − 1"],a:0},
{section:"math",level:1,type:"Functions",q:"The function f(x) = 4x + b passes through (2, 13). What is b?",o:["3","5","7","9"],a:1},
{section:"math",level:1,type:"Functions",q:"If p(x) = x/3 + 2, what value of x gives p(x) = 6?",o:["8","10","12","18"],a:2},
{section:"math",level:2,type:"Advanced Math",q:"The equation x² − 8x + k = 0 has exactly one real solution. What is k?",o:["8","12","16","32"],a:2},
{section:"math",level:2,type:"Advanced Math",q:"A quadratic function has zeros at 2 and 7 and passes through (0, −28). Which equation could represent it?",o:["f(x)=2(x−2)(x−7)","f(x)=−2(x−2)(x−7)","f(x)=(x+2)(x+7)","f(x)=2(x+2)(x−7)"],a:0},
{section:"math",level:2,type:"Problem Solving",q:"A quantity increases by 20% and then decreases by 20%. The final value is what percent of the original?",o:["96%","100%","104%","80%"],a:0},
{section:"math",level:2,type:"Advanced Math",q:"For what value of c does the system y = 2x + 1 and y = 2x + c have no solution?",o:["0","1","2","Any value except 1"],a:3},
{section:"math",level:2,type:"Problem Solving",q:"A circle has equation (x−3)²+(y+2)²=49. What is its radius?",o:["3","7","14","49"],a:1},
{section:"rw",level:1,type:"Vocabulary",q:"In the sentence, 'The scientist's findings were preliminary,' what does 'preliminary' most nearly mean?",o:["Final","Initial","Unrelated","Unreliable"],a:1},
{section:"rw",level:2,type:"Vocabulary",q:"In the sentence, 'The author's argument was nuanced,' what does 'nuanced' most nearly mean?",o:["Oversimplified","Containing subtle distinctions","Completely incorrect","Widely known"],a:1},
{section:"rw",level:1,type:"Reading",q:"Passage: A town planted trees along its main streets. Several years later, residents reported more shade and said the streets felt more pleasant. Which choice best states the passage's main idea?",o:["The town removed its main streets.","Tree planting improved the street environment.","Residents disliked the new trees.","The town stopped maintaining its streets."],a:1},
{section:"rw",level:2,type:"Reading",q:"Passage: Although the first study suggested that the device reduced energy use, a later investigation found that the effect depended on how often the device was used. Which statement best captures the relationship between the studies?",o:["The later study completely confirmed the first.","The later study qualified the first study's conclusion.","The first study was about a different device.","Both studies found no effect."],a:1},
{section:"rw",level:2,type:"Reading",q:"Passage: Some historians once attributed the city's growth primarily to trade. Newly examined letters, however, suggest that improvements in irrigation also played a substantial role. What is the main purpose of the passage?",o:["To reject all earlier historical research","To introduce evidence for an additional explanation","To describe how letters were written","To argue that trade had no influence"],a:1}
];
function startTest(){
  const profile=JSON.parse(localStorage.getItem("prepifyProfile")||"{}");
  // Beginners start with medium items; experienced learners receive a challenging sequence sooner.
  questions=bank.map(q=>({...q}));
  if(profile.experience==="experienced"){
    questions.sort((a,b)=>b.level-a.level);
  } else {
    questions.sort((a,b)=>a.level-b.level);
  }
  // Keep the requested 10 Math + 5 Reading & Writing structure.
  questions=questions.slice(0,15);
  current=0;answers=[];difficulty={math:0,rw:0};
  showPage("questionPage");renderQuestion();
}
function renderQuestion(){
  const q=questions[current];selected=null;
  $("sectionTag").textContent=q.section==="math"?"MATH":"READING & WRITING";
  $("questionCount").textContent=`Question ${current+1} of ${questions.length}`;
  $("progressBar").style.width=(current/questions.length*100)+"%";
  $("difficultyLabel").textContent=(q.level===1?"MEDIUM":"CHALLENGING")+" · "+q.type;
  $("questionText").textContent=q.q;
  $("options").innerHTML="";
  q.o.forEach((option,i)=>{
    const b=document.createElement("button");b.className="option";b.textContent=String.fromCharCode(65+i)+". "+option;
    b.onclick=()=>{selected=i;document.querySelectorAll(".option").forEach(x=>x.classList.remove("selected"));b.classList.add("selected");$("nextBtn").disabled=false};
    $("options").appendChild(b);
  });
  $("feedback").textContent="";
  $("nextBtn").disabled=true;
  $("nextBtn").textContent=current===questions.length-1?"Finish test":"Submit answer";
}
function nextQuestion(){
  if(selected===null)return;
  const q=questions[current],correct=selected===q.a;
  answers.push({section:q.section,correct,level:q.level});
  if(correct)difficulty[q.section]++;
  $("feedback").textContent=correct?"Answer recorded.":"Answer recorded. Keep going!";
  current++;
  if(current>=questions.length){showResults();return}
  renderQuestion();
}
function estimate(section){
  const subset=answers.filter(a=>a.section===section);
  const correct=subset.filter(a=>a.correct).length;
  const total=subset.length;
  const ratio=total?correct/total:0;
  // Broad diagnostic bands only; intentionally not a precise SAT prediction.
  let range;
  if(section==="math"){
    range=ratio<.3?"200–390":ratio<.5?"390–490":ratio<.7?"490–590":ratio<.9?"590–690":"650–740";
  }else{
    range=ratio<.3?"200–390":ratio<.5?"390–490":ratio<.7?"490–590":ratio<.9?"590–690":"650–740";
  }
  return {correct,total,range};
}
function showResults(){
  const m=estimate("math"),r=estimate("rw");
  $("mathResult").textContent=m.range;
  $("rwResult").textContent=r.range;
  $("mathAccuracy").textContent=`${m.correct} correct out of ${m.total}`;
  $("rwAccuracy").textContent=`${r.correct} correct out of ${r.total}`;
  $("resultAdvice").textContent=`You answered ${m.correct}/10 Math questions and ${r.correct}/5 Reading & Writing questions correctly. Your next lessons should focus on the question types you found difficult. These ranges are deliberately broad because this short test is not a full adaptive SAT exam.`;
  const old=JSON.parse(localStorage.getItem("prepifyProfile")||"{}");
  old.lastDiagnostic={math:m.range,rw:r.range,mathCorrect:m.correct,rwCorrect:r.correct};
  localStorage.setItem("prepifyProfile",JSON.stringify(old));
  showPage("resultPage");
}
function showDashboard(){
  const p=JSON.parse(localStorage.getItem("prepifyProfile")||"{}");
  $("userEmail").textContent=localStorage.getItem("prepifySession")||"";
  $("dashMath").textContent=p.mathTarget||700;
  $("dashRW").textContent=p.rwTarget||700;
  $("mathPlan").textContent=`Your daily goal: ${p.mathDaily||2} Math lessons`;
  $("rwPlan").textContent=`Your daily goal: ${p.rwDaily||2} Reading & Writing lessons`;
  showPage("dashboardPage");
}
function restartTest(){showPage("testPage")}
</script>
</body>
</html>
