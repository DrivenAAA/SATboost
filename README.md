
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify — Master Your SAT</title>
<meta name="description" content="Free SAT preparation platform with Math, Reading and Writing resources.">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
<script src="https://unpkg.com/lucide@latest"></script>

<style>
:root {
    --bg: #f7f8fc;
    --surface: #ffffff;
    --surface2: #f1f3fa;
    --text: #182039;
    --muted: #788198;
    --border: #e8eaf2;
    --primary: #635bff;
    --primary2: #817bff;
    --soft: #eeedff;
    --green: #16a67a;
    --shadow: 0 15px 45px rgba(30,35,80,.06);
    --font-scale: 1;
}

[data-theme="dark"] {
    --bg: #0c1020;
    --surface: #151b2e;
    --surface2: #202840;
    --text: #f0f2ff;
    --muted: #a0abc3;
    --border: #29324a;
    --primary: #8983ff;
    --primary2: #a49fff;
    --soft: #27264b;
    --green: #3ac99c;
    --shadow: 0 15px 45px rgba(0,0,0,.2);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
    scroll-padding-top: 90px;
}

body {
    font-family: 'Inter', sans-serif;
    background: var(--bg);
    color: var(--text);
    font-size: calc(15px * var(--font-scale));
    transition: background .3s, color .3s;
}

button, input {
    font-family: inherit;
}

button, a {
    -webkit-tap-highlight-color: transparent;
}

a {
    text-decoration: none;
    color: inherit;
}

button {
    cursor: pointer;
}

.container {
    width: 91%;
    max-width: 1200px;
    margin: auto;
}

/* NAVIGATION */

header {
    height: 78px;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
    position: sticky;
    top: 0;
    z-index: 100;
}

.navbar {
    height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-size: 27px;
    font-weight: 900;
    letter-spacing: -1.5px;
}

.logo span {
    color: var(--primary);
}

.nav-links {
    display: flex;
    align-items: center;
    gap: 32px;
}

.nav-links a {
    font-size: 13px;
    color: var(--muted);
    font-weight: 600;
    transition: .2s;
}

.nav-links a:hover {
    color: var(--primary);
}

.nav-actions {
    display: flex;
    align-items: center;
    gap: 10px;
}

.icon-btn {
    height: 39px;
    width: 39px;
    border-radius: 11px;
    background: var(--surface2);
    color: var(--text);
    border: 1px solid var(--border);
    display: grid;
    place-items: center;
    font-size: 15px;
}

.icon-btn:hover {
    border-color: var(--primary);
    color: var(--primary);
}

.mobile-menu {
    display: none;
}

/* BUTTONS */

.btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 9px;
    padding: 14px 22px;
    border: none;
    border-radius: 11px;
    font-size: 13px;
    font-weight: 700;
    transition: .25s;
}

.btn-primary {
    color: white;
    background: linear-gradient(120deg, #635bff, #827bff);
    box-shadow: 0 7px 20px #635bff35;
}

.btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 12px 25px #635bff45;
}

.btn-outline {
    color: var(--text);
    background: var(--surface);
    border: 1px solid var(--border);
}

.btn-outline:hover {
    border-color: var(--primary);
    color: var(--primary);
}

/* HERO */

.hero {
    padding: 85px 0 75px;
    overflow: hidden;
    position: relative;
}

.hero::before {
    content: "";
    position: absolute;
    width: 500px;
    height: 500px;
    background: radial-gradient(circle, #756cff20, transparent 70%);
    top: -180px;
    right: -100px;
    pointer-events: none;
}

.hero-grid {
    display: grid;
    grid-template-columns: 1.15fr .85fr;
    align-items: center;
    gap: 60px;
}

.eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: var(--soft);
    color: var(--primary);
    padding: 9px 14px;
    border-radius: 30px;
    font-size: 10px;
    font-weight: 800;
    letter-spacing: 1px;
}

.eyebrow i {
    width: 14px;
    height: 14px;
}

.hero h1 {
    font-size: clamp(43px, 5.5vw, 68px);
    line-height: 1.08;
    letter-spacing: -3.5px;
    margin: 25px 0;
    font-weight: 900;
}

.gradient-text {
    background: linear-gradient(110deg, #635bff, #a17bff);
    -webkit-background-clip: text;
    color: transparent;
}

.hero-description {
    color: var(--muted);
    font-size: 15px;
    line-height: 1.9;
    max-width: 510px;
}

.hero-buttons {
    display: flex;
    gap: 13px;
    margin-top: 32px;
    flex-wrap: wrap;
}

.hero-note {
    display: flex;
    gap: 22px;
    margin-top: 32px;
    flex-wrap: wrap;
    color: var(--muted);
    font-size: 11px;
    font-weight: 600;
}

.hero-note span {
    display: flex;
    align-items: center;
    gap: 6px;
}

.hero-note i {
    color: var(--green);
    width: 15px;
}

/* DASHBOARD CARD */

.dashboard {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 27px;
    border-radius: 23px;
    box-shadow: var(--shadow);
    position: relative;
    animation: float 5s ease-in-out infinite;
}

@keyframes float {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-9px); }
}

.dash-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.dash-top h3 {
    font-size: 13px;
}

.live {
    font-size: 10px;
    color: var(--green);
    background: var(--surface2);
    padding: 7px 10px;
    border-radius: 20px;
    font-weight: 700;
}

.dash-title {
    font-size: 12px;
    color: var(--muted);
    margin-top: 28px;
}

.dash-score {
    display: flex;
    align-items: center;
    gap: 20px;
    margin: 15px 0 25px;
}

.score-number {
    font-size: 47px;
    font-weight: 900;
    letter-spacing: -2px;
}

.score-label {
    color: var(--muted);
    font-size: 11px;
    line-height: 1.7;
}

.score-label strong {
    color: var(--green);
}

.dash-divider {
    height: 1px;
    background: var(--border);
    margin: 20px 0;
}

.skill {
    margin: 19px 0;
}

.skill-info {
    display: flex;
    justify-content: space-between;
    font-size: 12px;
    font-weight: 600;
    margin-bottom: 10px;
}

.skill-info span:last-child {
    color: var(--muted);
}

.skill-bar {
    height: 8px;
    background: var(--surface2);
    border-radius: 20px;
    overflow: hidden;
}

.skill-fill {
    height: 100%;
    border-radius: 20px;
    background: linear-gradient(90deg, #635bff, #a18aff);
}

.skill-fill.green {
    background: linear-gradient(90deg, #13a77c, #53d9ac);
}

.dash-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 11px;
    color: var(--muted);
    margin-top: 23px;
}

/* STATS */

.stats-section {
    padding: 0 0 60px;
}

.stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 15px;
}

.stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 15px;
    padding: 23px;
}

.stat-icon {
    width: 38px;
    height: 38px;
    border-radius: 11px;
    background: var(--soft);
    color: var(--primary);
    display: grid;
    place-items: center;
    margin-bottom: 16px;
}

.stat-card h3 {
    font-size: 25px;
    letter-spacing: -1px;
}

.stat-card p {
    color: var(--muted);
    font-size: 11px;
    margin-top: 6px;
}

/* SECTION HEADINGS */

.section {
    padding: 85px 0;
}

.section-heading {
    text-align: center;
    margin-bottom: 45px;
}

.section-heading h2 {
    font-size: clamp(28px, 4vw, 39px);
    letter-spacing: -1.5px;
    margin: 15px 0;
}

.section-heading p {
    color: var(--muted);
    font-size: 14px;
    line-height: 1.8;
}

/* COURSES */

.course-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 22px;
}

.course-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 19px;
    padding: 30px;
    transition: .3s;
    position: relative;
    overflow: hidden;
}

.course-card:hover {
    transform: translateY(-6px);
    box-shadow: var(--shadow);
    border-color: var(--primary2);
}

.course-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.course-icon {
    width: 53px;
    height: 53px;
    border-radius: 14px;
    display: grid;
    place-items: center;
}

.course-icon i {
    width: 25px;
    height: 25px;
}

.purple {
    background: #efedff;
    color: #635bff;
}

.mint {
    background: #e1f8ef;
    color: #159e72;
}

.course-tag {
    color: var(--muted);
    font-size: 10px;
    background: var(--surface2);
    padding: 7px 10px;
    border-radius: 20px;
}

.course-card h3 {
    font-size: 22px;
    margin: 25px 0 10px;
}

.course-card p {
    color: var(--muted);
    font-size: 13px;
    line-height: 1.8;
}

.course-topics {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin: 22px 0;
}

.topic {
    background: var(--surface2);
    color: var(--muted);
    padding: 8px 11px;
    border-radius: 8px;
    font-size: 10px;
    font-weight: 600;
}

.course-link {
    color: var(--primary);
    font-size: 12px;
    font-weight: 800;
    display: inline-flex;
    align-items: center;
    gap: 7px;
}

/* PRACTICE */

.practice-section {
    background: var(--surface2);
}

.practice-layout {
    display: grid;
    grid-template-columns: .85fr 1.15fr;
    gap: 45px;
    align-items: center;
}

.practice-info h2 {
    font-size: 38px;
    letter-spacing: -1.5px;
    margin: 18px 0;
}

.practice-info p {
    color: var(--muted);
    line-height: 1.9;
    font-size: 14px;
}

.question-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 19px;
    padding: 28px;
    box-shadow: var(--shadow);
}

.question-meta {
    display: flex;
    justify-content: space-between;
    color: var(--muted);
    font-size: 11px;
    margin-bottom: 22px;
}

.question-card h3 {
    font-size: 17px;
    line-height: 1.7;
    margin-bottom: 22px;
}

.answers {
    display: grid;
    gap: 10px;
}

.answer {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 11px;
    padding: 14px;
    text-align: left;
    color: var(--text);
    font-size: 13px;
    display: flex;
    align-items: center;
    gap: 12px;
    transition: .2s;
}

.answer:hover:not(:disabled) {
    border-color: var(--primary);
    background: var(--soft);
}

.answer-letter {
    width: 27px;
    height: 27px;
    border: 1px solid var(--border);
    border-radius: 8px;
    display: grid;
    place-items: center;
    font-weight: 700;
    flex-shrink: 0;
}

.answer.correct {
    border-color: var(--green);
    background: #16a67a12;
}

.answer.wrong {
    border-color: #ef6565;
    background: #ef656512;
}

.answer:disabled {
    cursor: default;
    opacity: .9;
}

.feedback {
    display: none;
    padding: 14px;
    margin-top: 15px;
    border-radius: 10px;
    font-size: 12px;
    line-height: 1.7;
}

.feedback.show {
    display: block;
}

.feedback.success {
    color: var(--green);
    background: #16a67a12;
}

.feedback.error {
    color: #e16a6a;
    background: #e16a6a12;
}

.question-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 22px;
}

.question-bottom span {
    color: var(--muted);
    font-size: 11px;
}

/* RESOURCE SEARCH */

.resources {
    background: var(--bg);
}

.search-box {
    max-width: 550px;
    margin: 0 auto 30px;
    position: relative;
}

.search-box input {
    width: 100%;
    background: var(--surface);
    color: var(--text);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px 45px;
    outline: none;
    font-size: 13px;
}

.search-box input:focus {
    border-color: var(--primary);
}

.search-box i {
    position: absolute;
    left: 16px;
    top: 16px;
    color: var(--muted);
    width: 18px;
}

.resource-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 17px;
}

.resource-card {
    padding: 24px;
    border-radius: 15px;
    border: 1px solid var(--border);
    background: var(--surface);
    transition: .25s;
}

.resource-card:hover {
    transform: translateY(-4px);
    border-color: var(--primary);
}

.resource-card .resource-icon {
    color: var(--primary);
    margin-bottom: 18px;
}

.resource-card h3 {
    font-size: 15px;
    margin-bottom: 8px;
}

.resource-card p {
    color: var(--muted);
    font-size: 12px;
    line-height: 1.7;
}

.resource-card a {
    color: var(--primary);
    font-size: 11px;
    font-weight: 800;
    display: inline-block;
    margin-top: 17px;
}

.no-results {
    display: none;
    text-align: center;
    color: var(--muted);
    padding: 30px;
    font-size: 13px;
}

/* MISSION */

.mission {
    padding: 80px 0;
}

.mission-box {
    background: linear-gradient(120deg, #29245f, #655bda);
    color: white;
    border-radius: 23px;
    padding: 55px;
    text-align: center;
}

.mission-box h2 {
    font-size: 34px;
    letter-spacing: -1px;
    margin: 17px 0;
}

.mission-box p {
    color: #dddafa;
    max-width: 650px;
    margin: auto;
    line-height: 1.9;
    font-size: 13px;
}

/* FOOTER */

footer {
    padding: 45px 0;
    background: var(--surface);
    border-top: 1px solid var(--border);
}

.footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
}

.footer-content p {
    color: var(--muted);
    font-size: 11px;
}

/* FONT SETTINGS */

.font-controls {
    display: flex;
    align-items: center;
    gap: 6px;
    background: var(--surface2);
    padding: 4px;
    border-radius: 10px;
    border: 1px solid var(--border);
}

.font-controls button {
    border: none;
    background: transparent;
    color: var(--text);
    padding: 7px;
    font-size: 11px;
    font-weight: 700;
}

/* ANIMATIONS */

.reveal {
    animation: reveal .7s ease both;
}

@keyframes reveal {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* MOBILE */

@media(max-width: 850px) {
    .nav-links {
        gap: 15px;
    }

    .nav-links a {
        font-size: 11px;
    }

    .hero-grid {
        gap: 35px;
    }

    .hero h1 {
        font-size: 48px;
    }

    .stats-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .resource-grid {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media(max-width: 650px) {
    header {
        height: 70px;
    }

    .nav-links {
        display: none;
        position: absolute;
        top: 69px;
        left: 0;
        width: 100%;
        background: var(--surface);
        padding: 20px 5%;
        border-bottom: 1px solid var(--border);
        flex-direction: column;
        align-items: flex-start;
        gap: 22px;
    }

    .nav-links.open {
        display: flex;
    }

    .mobile-menu {
        display: grid;
    }

    .nav-button {
        display: none;
    }

    .hero {
        padding: 65px 0;
    }

    .hero-grid, .practice-layout {
        grid-template-columns: 1fr;
    }

    .hero h1 {
        font-size: 44px;
        letter-spacing: -2px;
    }

    .dashboard {
        padding: 22px;
    }

    .course-grid {
        grid-template-columns: 1fr;
    }

    .section {
        padding: 65px 0;
    }

    .practice-info h2 {
        font-size: 31px;
    }

    .resource-grid {
        grid-template-columns: 1fr;
    }

    .mission-box {
        padding: 38px 22px;
    }

    .mission-box h2 {
        font-size: 27px;
    }

    .footer-content {
        flex-direction: column;
        align-items: flex-start;
    }

    .font-controls {
        display: none;
    }
}

@media(prefers-reduced-motion: reduce) {
    *, *::before, *::after {
        animation-duration: .01ms !important;
        transition-duration: .01ms !important;
        scroll-behavior: auto !important;
    }
}
</style>
</head>

<body>

<header>
<div class="container navbar">

    <a href="#home" class="logo">Prepify<span>.</span></a>

    <nav class="nav-links" id="navLinks">
        <a href="#home">Home</a>
        <a href="#courses">Courses</a>
        <a href="#practice">Practice</a>
        <a href="#resources">Resources</a>
        <a href="#about">About</a>
    </nav>

    <div class="nav-actions">

        <div class="font-controls" title="Change text size">
            <button onclick="changeFont(-0.05)">A-</button>
            <button onclick="changeFont(0.05)">A+</button>
        </div>

        <button class="icon-btn" id="themeToggle" aria-label="Toggle dark mode">
            <i data-lucide="moon"></i>
        </button>

        <a href="#courses" class="btn btn-primary nav-button">
            Get Started
        </a>

        <button class="icon-btn mobile-menu" id="menuToggle" aria-label="Open menu">
            <i data-lucide="menu"></i>
        </button>

    </div>
</div>
</header>


<main>

<!-- HERO -->

<section class="hero" id="home">
<div class="container hero-grid">

    <div class="reveal">

        <div class="eyebrow">
            <i data-lucide="sparkles"></i>
            YOUR SAT JOURNEY STARTS HERE
        </div>

        <h1>
            Think Bigger.<br>
            Score <span class="gradient-text">Higher.</span>
        </h1>

        <p class="hero-description">
            Your journey to a better SAT score begins with the right
            resources. Learn, practice and improve with our free
            educational platform.
        </p>

        <div class="hero-buttons">
            <a href="#courses" class="btn btn-primary">
                Explore Courses <i data-lucide="arrow-right"></i>
            </a>

            <a href="#practice" class="btn btn-outline">
                Try a Question <i data-lucide="play"></i>
            </a>
        </div>

        <div class="hero-note">
            <span><i data-lucide="check-circle"></i> Free learning resources</span>
            <span><i data-lucide="check-circle"></i> Learn at your own pace</span>
        </div>

    </div>


    <div class="dashboard reveal">

        <div class="dash-top">
            <h3>My Learning Overview</h3>
            <span class="live">● READY TO LEARN</span>
        </div>

        <p class="dash-title">YOUR TARGET SCORE</p>

        <div class="dash-score">
            <div class="score-number">1600</div>
            <div class="score-label">
                SAT Maximum Score<br>
                <strong>Set your goal!</strong>
            </div>
        </div>

        <div class="dash-divider"></div>

        <div class="skill">
            <div class="skill-info">
                <span>Math</span>
                <span>Practice section</span>
            </div>
            <div class="skill-bar">
                <div class="skill-fill" style="width:80%"></div>
            </div>
        </div>

        <div class="skill">
            <div class="skill-info">
                <span>Reading & Writing</span>
                <span>Practice section</span>
            </div>
            <div class="skill-bar">
                <div class="skill-fill green" style="width:70%"></div>
            </div>
        </div>

        <div class="dash-bottom">
            <span><i data-lucide="book-open"></i> Keep learning</span>
            <span>One step at a time →</span>
        </div>

    </div>

</div>
</section>


<!-- STATS -->

<section class="stats-section">
<div class="container stats-grid">

    <div class="stat-card">
        <div class="stat-icon"><i data-lucide="book-open"></i></div>
        <h3>2</h3>
        <p>Core SAT Sections</p>
    </div>

    <div class="stat-card">
        <div class="stat-icon"><i data-lucide="globe"></i></div>
        <h3>Global</h3>
        <p>Learning Community</p>
    </div>

    <div class="stat-card">
        <div class="stat-icon"><i data-lucide="clock"></i></div>
        <h3>24/7</h3>
        <p>Learn Anytime</p>
    </div>

    <div class="stat-card">
        <div class="stat-icon"><i data-lucide="heart"></i></div>
        <h3>Free</h3>
        <p>Educational Access</p>
    </div>

</div>
</section>


<!-- COURSES -->

<section class="section" id="courses">
<div class="container">

    <div class="section-heading">
        <span class="eyebrow">EXPLORE YOUR POTENTIAL</span>
        <h2>Everything You Need to Master the SAT</h2>
        <p>Build your skills with focused learning and consistent practice.</p>
    </div>

    <div class="course-grid">

        <div class="course-card">

            <div class="course-top">
                <div class="course-icon purple">
                    <i data-lucide="calculator"></i>
                </div>
                <span class="course-tag">SAT SECTION 01</span>
            </div>

            <h3>SAT Math</h3>

            <p>
                Develop your mathematical thinking and master
                the concepts tested on the digital SAT.
            </p>

            <div class="course-topics">
                <span class="topic">Algebra</span>
                <span class="topic">Advanced Math</span>
                <span class="topic">Geometry</span>
                <span class="topic">Data Analysis</span>
            </div>

            <a href="#practice" class="course-link">
                Explore Math <i data-lucide="arrow-right"></i>
            </a>

        </div>


        <div class="course-card">

            <div class="course-top">
                <div class="course-icon mint">
                    <i data-lucide="book-text"></i>
                </div>
                <span class="course-tag">SAT SECTION 02</span>
            </div>

            <h3>Reading & Writing</h3>

            <p>
                Strengthen your grammar, reading comprehension,
                vocabulary and analytical thinking.
            </p>

            <div class="course-topics">
                <span class="topic">Grammar</span>
                <span class="topic">Vocabulary</span>
                <span class="topic">Reading</span>
                <span class="topic">Rhetoric</span>
            </div>

            <a href="#resources" class="course-link">
                Explore English <i data-lucide="arrow-right"></i>
            </a>

        </div>

    </div>
</div>
</section>


<!-- PRACTICE -->

<section class="section practice-section" id="practice">
<div class="container practice-layout">

    <div class="practice-info">
        <span class="eyebrow">INTERACTIVE PRACTICE</span>

        <h2>Learn by Doing. Improve by Practicing.</h2>

        <p>
            Test your knowledge with original SAT-style sample
            questions. Choose an answer and get instant feedback
            with an explanation.
        </p>

        <br>

        <span style="color:var(--muted);font-size:12px">
            <i data-lucide="info" style="width:14px;vertical-align:middle"></i>
            These are original practice questions, not official College Board questions.
        </span>
    </div>


    <div class="question-card">

        <div class="question-meta">
            <span>SAT MATH • SAMPLE QUESTION</span>
            <span id="questionNumber">QUESTION 1</span>
        </div>

        <h3 id="questionText">
            If 3x + 7 = 22, what is the value of x?
        </h3>

        <div class="answers" id="answers">

            <button class="answer" onclick="checkAnswer(0)">
                <span class="answer-letter">A</span>
                <span>3</span>
            </button>

            <button class="answer" onclick="checkAnswer(1)">
                <span class="answer-letter">B</span>
                <span>5</span>
            </button>

            <button class="answer" onclick="checkAnswer(2)">
                <span class="answer-letter">C</span>
                <span>7</span>
            </button>

            <button class="answer" onclick="checkAnswer(3)">
                <span class="answer-letter">D</span>
                <span>9</span>
            </button>

        </div>

        <div class="feedback" id="feedback"></div>

        <div class="question-bottom">
            <span id="questionStatus">Select your answer</span>

            <button class="btn btn-primary" id="nextQuestion" onclick="nextQuestion()" style="display:none">
                Next Question <i data-lucide="arrow-right"></i>
            </button>
        </div>

    </div>

</div>
</section>


<!-- RESOURCES -->

<section class="section resources" id="resources">
<div class="container">

    <div class="section-heading">
        <span class="eyebrow">YOUR LEARNING TOOLKIT</span>
        <h2>Explore Learning Resources</h2>
        <p>Find the resources you need to make your preparation more effective.</p>
    </div>

    <div class="search-box">
        <i data-lucide="search"></i>
        <input type="text" id="resourceSearch" placeholder="Search resources...">
    </div>

    <div class="resource-grid" id="resourceGrid">

        <div class="resource-card" data-search="algebra math equations">
            <div class="resource-icon"><i data-lucide="calculator"></i></div>
            <h3>Algebra Essentials</h3>
            <p>Build a strong foundation in equations, expressions and functions.</p>
            <a href="#practice">Explore →</a>
        </div>

        <div class="resource-card" data-search="grammar english writing">
            <div class="resource-icon"><i data-lucide="languages"></i></div>
            <h3>Grammar Guide</h3>
            <p>Understand essential grammar rules and sentence structure.</p>
            <a href="#practice">Explore →</a>
        </div>

        <div class="resource-card" data-search="vocabulary english words">
            <div class="resource-icon"><i data-lucide="book-a"></i></div>
            <h3>Vocabulary Builder</h3>
            <p>Develop your vocabulary and improve your understanding of words.</p>
            <a href="#practice">Explore →</a>
        </div>

        <div class="resource-card" data-search="geometry math shapes">
            <div class="resource-icon"><i data-lucide="shapes"></i></div>
            <h3>Geometry Basics</h3>
            <p>Review shapes, angles, area and other mathematical concepts.</p>
            <a href="#practice">Explore →</a>
        </div>

        <div class="resource-card" data-search="reading comprehension passages">
            <div class="resource-icon"><i data-lucide="book-open"></i></div>
            <h3>Reading Practice</h3>
            <p>Improve your ability to analyze passages and understand ideas.</p>
            <a href="#practice">Explore →</a>
        </div>

        <div class="resource-card" data-search="data analysis statistics math">
            <div class="resource-icon"><i data-lucide="chart-no-axes-combined"></i></div>
            <h3>Data Analysis</h3>
            <p>Practice interpreting tables, graphs and statistical information.</p>
            <a href="#practice">Explore →</a>
        </div>

    </div>

    <div class="no-results" id="noResults">
        No resources found. Try another search.
    </div>

</div>
</section>


<!-- MISSION -->

<section class="mission" id="about">
<div class="container">

    <div class="mission-box">
        <span class="eyebrow" style="background:#ffffff20;color:#fff">
            OUR MISSION
        </span>

        <h2>Education Should Have No Limits.</h2>

        <p>
            We believe every student deserves access to quality
            educational resources. Prepify aims to make SAT
            preparation more accessible, regardless of financial background.
        </p>

        <br>

        <a href="#courses" class="btn" style="background:white;color:#5149bd">
            Start Your Journey <i data-lucide="arrow-right"></i>
        </a>
    </div>

</div>
</section>

</main>


<!-- FOOTER -->

<footer>
<div class="container footer-content">

    <a href="#home" class="logo">Prepify<span>.</span></a>

    <p>Making SAT preparation accessible to everyone.</p>

    <p>© 2026 Prepify. Educational project.</p>

</div>
</footer>


<script>

// ICONS
lucide.createIcons();


// DARK / LIGHT MODE

const themeToggle = document.getElementById("themeToggle");

function setTheme(theme) {
    document.documentElement.setAttribute("data-theme", theme);
    localStorage.setItem("prepify-theme", theme);

    themeToggle.innerHTML = theme === "dark"
        ? '<i data-lucide="sun"></i>'
        : '<i data-lucide="moon"></i>';

    lucide.createIcons();
}

const savedTheme = localStorage.getItem("prepify-theme") || "light";
setTheme(savedTheme);

themeToggle.addEventListener("click", () => {
    const current = document.documentElement.getAttribute("data-theme");
    setTheme(current === "dark" ? "light" : "dark");
});


// FONT SIZE SETTINGS

let fontSize = Number(localStorage.getItem("prepify-font")) || 1;

function applyFont() {
    document.documentElement.style.setProperty("--font-scale", fontSize);
    localStorage.setItem("prepify-font", fontSize);
}

function changeFont(amount) {
    fontSize = Math.min(1.2, Math.max(0.9, fontSize + amount));
    fontSize = Number(fontSize.toFixed(2));
    applyFont();
}

applyFont();


// MOBILE MENU

const menuToggle = document.getElementById("menuToggle");
const navLinks = document.getElementById("navLinks");

menuToggle.addEventListener("click", () => {
    navLinks.classList.toggle("open");

    menuToggle.innerHTML = navLinks.classList.contains("open")
        ? '<i data-lucide="x"></i>'
        : '<i data-lucide="menu"></i>';

    lucide.createIcons();
});

document.querySelectorAll(".nav-links a").forEach(link => {
    link.addEventListener("click", () => {
        navLinks.classList.remove("open");
        menuToggle.innerHTML = '<i data-lucide="menu"></i>';
        lucide.createIcons();
    });
});


// RESOURCE SEARCH

const searchInput = document.getElementById("resourceSearch");
const resourceCards = document.querySelectorAll(".resource-card");
const noResults = document.getElementById("noResults");

searchInput.addEventListener("input", () => {
    const query = searchInput.value.toLowerCase().trim();
    let visible = 0;

    resourceCards.forEach(card => {
        const content = (
            card.innerText + " " + card.dataset.search
        ).toLowerCase();

        const match = content.includes(query);

        card.style.display = match ? "block" : "none";

        if (match) visible++;
    });

    noResults.style.display = visible === 0 ? "block" : "none";
});


// INTERACTIVE PRACTICE QUESTIONS

const questions = [
    {
        text: "If 3x + 7 = 22, what is the value of x?",
        options: ["3", "5", "7", "9"],
        correct: 1,
        explanation: "Subtract 7 from both sides: 3x = 15. Then divide by 3. Therefore, x = 5."
    },
    {
        text: "If 2(x + 4) = 18, what is the value of x?",
        options: ["4", "5", "6", "7"],
        correct: 1,
        explanation: "Divide both sides by 2: x + 4 = 9. Subtract 4. Therefore, x = 5."
    },
    {
        text: "What is the slope of the line y = 4x + 3?",
        options: ["3", "4", "-3", "-4"],
        correct: 1,
        explanation: "In slope-intercept form y = mx + b, m represents the slope. Here, m = 4."
    },
    {
        text: "If x² = 49 and x is positive, what is x?",
        options: ["5", "6", "7", "8"],
        correct: 2,
        explanation: "The square root of 49 is 7. Since x is positive, x = 7."
    }
];

let currentQuestion = 0;
let answered = false;

function loadQuestion() {
    const q = questions[currentQuestion];

    document.getElementById("questionText").textContent = q.text;
    document.getElementById("questionNumber").textContent =
        "QUESTION " + (currentQuestion + 1);

    document.getElementById("questionStatus").textContent =
        "Select your answer";

    document.getElementById("feedback").className = "feedback";
    document.getElementById("feedback").textContent = "";

    document.getElementById("nextQuestion").style.display = "none";

    const answers = document.getElementById("answers");
    answers.innerHTML = "";

    q.options.forEach((option, index) => {
        const button = document.createElement("button");
        button.className = "answer";

        button.innerHTML = `
            <span class="answer-letter">${String.fromCharCode(65 + index)}</span>
            <span>${option}</span>
        `;

        button.addEventListener("click", () => checkAnswer(index));
        answers.appendChild(button);
    });

    answered = false;
}

function checkAnswer(selected) {
    if (answered) return;

    answered = true;

    const q = questions[currentQuestion];
    const buttons = document.querySelectorAll(".answer");
    const feedback = document.getElementById("feedback");

    buttons.forEach((button, index) => {
        button.disabled = true;

        if (index === q.correct) {
            button.classList.add("correct");
        }

        if (index === selected && selected !== q.correct) {
            button.classList.add("wrong");
        }
    });

    if (selected === q.correct) {
        feedback.className = "feedback show success";
        feedback.textContent = "Correct! " + q.explanation;
        document.getElementById("questionStatus").textContent =
            "Great work!";
    } else {
        feedback.className = "feedback show error";
        feedback.textContent = "Not quite. " + q.explanation;
        document.getElementById("questionStatus").textContent =
            "Review the explanation.";
    }

    document.getElementById("nextQuestion").style.display = "inline-flex";

    lucide.createIcons();
}

function nextQuestion() {
    currentQuestion = (currentQuestion + 1) % questions.length;
    loadQuestion();
}

loadQuestion();

</script>

</body>
</html>
