
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prepify | Free SAT Preparation</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    font-family: 'Inter', sans-serif;
    color: #172033;
}

.container {
    width: 90%;
    max-width: 1180px;
    margin: auto;
}

.navbar {
    padding: 22px 0;
    border-bottom: 1px solid #eee;
}

.nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-size: 27px;
    font-weight: 800;
    color: #172033;
    text-decoration: none;
}

.logo span {
    color: #4169e1;
}

nav {
    display: flex;
    gap: 30px;
}

nav a {
    text-decoration: none;
    color: #647084;
    font-size: 14px;
}

.nav-button, .primary-button {
    background: #4169e1;
    color: white;
    padding: 14px 22px;
    border-radius: 9px;
    text-decoration: none;
    font-size: 14px;
    font-weight: 600;
}

.hero {
    background: #f6f8ff;
    padding: 100px 0;
}

.hero-content {
    display: grid;
    grid-template-columns: 1.1fr .9fr;
    gap: 70px;
    align-items: center;
}

.tag {
    color: #4169e1;
    font-size: 11px;
    font-weight: 800;
    letter-spacing: 1.5px;
}

h1 {
    font-size: 58px;
    line-height: 1.15;
    margin: 22px 0;
}

h1 span {
    color: #4169e1;
    display: block;
}

.hero-text p {
    color: #69758a;
    line-height: 1.8;
}

.buttons {
    display: flex;
    gap: 15px;
    margin-top: 30px;
}

.secondary-button {
    padding: 14px 22px;
    border: 1px solid #dce2ee;
    border-radius: 9px;
    text-decoration: none;
    color: #172033;
    font-size: 14px;
}

.stats {
    display: flex;
    gap: 45px;
    margin-top: 55px;
}

.stats h3 {
    font-size: 23px;
}

.stats p {
    font-size: 12px;
    color: #8993a5;
    margin-top: 6px;
}

.hero-card {
    background: white;
    padding: 30px;
    border-radius: 20px;
    box-shadow: 0 20px 60px #1e326414;
}

.card-top {
    display: flex;
    justify-content: space-between;
    font-size: 10px;
    font-weight: 700;
    color: #8792a5;
}

.status {
    color: #16a36a;
}

.score {
    width: 175px;
    height: 175px;
    border-radius: 50%;
    border: 12px solid #e6ebff;
    border-top-color: #4169e1;
    border-right-color: #4169e1;
    margin: 35px auto;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.score h2 {
    font-size: 35px;
}

.score p {
    font-size: 10px;
    color: #8993a5;
}

.hero-card h3, .hero-card > p {
    text-align: center;
    margin-bottom: 10px;
}

.hero-card > p {
    color: #8993a5;
    font-size: 12px;
    line-height: 1.6;
}

.progress-item {
    margin-top: 25px;
}

.progress-label {
    display: flex;
    justify-content: space-between;
    font-size: 12px;
    margin-bottom: 9px;
}

.progress-bar {
    height: 7px;
    background: #edf0f7;
    border-radius: 10px;
    overflow: hidden;
}

.progress-bar div {
    height: 100%;
    background: #4169e1;
    width: 80%;
}

.progress-bar .green {
    background: #18a783;
    width: 70%;
}

section {
    padding: 90px 0;
}

.section-heading {
    text-align: center;
    margin-bottom: 50px;
}

.section-heading h2, .practice h2, .about h2 {
    font-size: 35px;
    margin: 17px 0;
}

.section-heading p, .practice p, .about p {
    color: #778196;
    line-height: 1.8;
    font-size: 14px;
}

.course-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 25px;
}

.course-card {
    padding: 35px;
    border: 1px solid #edf0f5;
    border-radius: 15px;
    transition: .3s;
}

.course-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 35px #1e326412;
}

.course-icon {
    width: 55px;
    height: 55px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 25px;
}

.math-icon {
    background: #eaf0ff;
    color: #4169e1;
}

.reading-icon {
    background: #e4f8f1;
    color: #159b70;
}

.course-card h3 {
    font-size: 21px;
    margin-bottom: 13px;
}

.course-card p {
    color: #778196;
    font-size: 14px;
    line-height: 1.8;
    margin-bottom: 22px;
}

.course-card a {
    text-decoration: none;
    color: #4169e1;
    font-size: 13px;
    font-weight: 700;
}

.practice {
    background: #f6f8ff;
}

.practice-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 30px;
}

.practice-content div {
    max-width: 550px;
}

.about-content {
    text-align: center;
    max-width: 750px;
}

footer {
    background: #101a30;
    color: white;
    padding: 45px 0;
}

.footer-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
}

footer .logo {
    color: white;
}

footer p {
    color: #a4aec0;
    font-size: 12px;
}

@media(max-width: 768px) {
    .nav-content {
        flex-wrap: wrap;
        gap: 20px;
    }

    nav {
        order: 3;
        width: 100%;
        justify-content: space-between;
        gap: 10px;
    }

    nav a {
        font-size: 12px;
    }

    .hero {
        padding: 65px 0;
    }

    .hero-content {
        grid-template-columns: 1fr;
        gap: 45px;
    }

    h1 {
        font-size: 42px;
    }

    .stats {
        gap: 25px;
    }

    .course-grid {
        grid-template-columns: 1fr;
    }

    .practice-content, .footer-content {
        flex-direction: column;
        align-items: flex-start;
    }

    .section-heading h2, .practice h2, .about h2 {
        font-size: 28px;
    }
}
</style>
</head>

<body>

<header class="navbar">
<div class="container nav-content">
    <a href="#" class="logo">Prepify<span>.</span></a>

    <nav>
        <a href="#home">Home</a>
        <a href="#courses">Courses</a>
        <a href="#practice">Practice</a>
        <a href="#about">About</a>
    </nav>

    <a href="#courses" class="nav-button">Start Learning</a>
</div>
</header>

<main>

<section class="hero" id="home">
<div class="container hero-content">

    <div class="hero-text">
        <span class="tag">YOUR FREE SAT PREPARATION PLATFORM</span>

        <h1>Your SAT Journey <span>Starts Here.</span></h1>

        <p>
            Prepare smarter, practice harder, and achieve your
            dream SAT score with free learning resources.
        </p>

        <div class="buttons">
            <a href="#courses" class="primary-button">Explore Courses</a>
            <a href="#about" class="secondary-button">Learn More</a>
        </div>

        <div class="stats">
            <div>
                <h3>100%</h3>
                <p>Free Resources</p>
            </div>
            <div>
                <h3>2</h3>
                <p>Main Sections</p>
            </div>
            <div>
                <h3>24/7</h3>
                <p>Learn Anytime</p>
            </div>
        </div>
    </div>

    <div class="hero-card">
        <div class="card-top">
            <span>YOUR SAT DASHBOARD</span>
            <span class="status">● Ready</span>
        </div>

        <div class="score">
            <div>
                <h2>1600</h2>
                <p>YOUR GOAL</p>
            </div>
        </div>

        <h3>Build your SAT success</h3>
        <p>Every practice session brings you closer to your goal.</p>

        <div class="progress-item">
            <div class="progress-label">
                <span>Math</span>
                <span>750+</span>
            </div>
            <div class="progress-bar"><div></div></div>
        </div>

        <div class="progress-item">
            <div class="progress-label">
                <span>Reading & Writing</span>
                <span>750+</span>
            </div>
            <div class="progress-bar"><div class="green"></div></div>
        </div>
    </div>

</div>
</section>

<section id="courses">
<div class="container">

    <div class="section-heading">
        <span class="tag">WHAT YOU WILL LEARN</span>
        <h2>Prepare for Every Section</h2>
        <p>Everything you need to improve your SAT performance.</p>
    </div>

    <div class="course-grid">

        <div class="course-card">
            <div class="course-icon math-icon">∑</div>
            <h3>SAT Math</h3>
            <p>Master algebra, advanced math, problem-solving and geometry.</p>
            <a href="#practice">Explore Math →</a>
        </div>

        <div class="course-card">
            <div class="course-icon reading-icon">Aa</div>
            <h3>Reading & Writing</h3>
            <p>Improve grammar, vocabulary, comprehension and analytical skills.</p>
            <a href="#practice">Explore English →</a>
        </div>

    </div>
</div>
</section>

<section class="practice" id="practice">
<div class="container practice-content">
    <div>
        <span class="tag">PRACTICE MAKES PROGRESS</span>
        <h2>Test Your Knowledge</h2>
        <p>Practice SAT-style questions and strengthen your skills one question at a time.</p>
    </div>

    <a href="#courses" class="primary-button">Start Practicing →</a>
</div>
</section>

<section id="about">
<div class="container about-content">
    <span class="tag">OUR MISSION</span>
    <h2>Quality SAT Preparation Should Be Accessible to Everyone.</h2>
    <p>
        Our mission is to provide free educational resources
        and help students around the world prepare for the SAT
        regardless of their financial background.
    </p>
</div>
</section>

</main>

<footer>
<div class="container footer-content">
    <a href="#" class="logo">Prepify<span>.</span></a>
    <p>Making SAT preparation accessible to everyone.</p>
    <p>© 2026 Prepify. Educational project.</p>
</div>
</footer>

<script>
document.querySelectorAll('a[href^="#"]').forEach(link => {
    link.addEventListener("click", function(event) {
        const target = document.querySelector(this.getAttribute("href"));

        if (target) {
            event.preventDefault();
            target.scrollIntoView({ behavior: "smooth" });
        }
    });
});

console.log("Welcome to Prepify!");
</script>

</body>
</html>
