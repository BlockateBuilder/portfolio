<html lang="en"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&amp;family=DM+Sans:wght@300;400;500&amp;display=swap" rel="stylesheet">

  <style>
    /* =============================================
       CSS CUSTOM PROPERTIES (variables)
       Change these to instantly retheme the whole site!
    ============================================= */
    :root {
      --color-bg:       #0f0f0f;
      --color-surface:  #1a1a1a;
      --color-accent:   #835df5;   /* ← try changing this to any color you like */
      --color-text:     #e8e8e8;
      --color-muted:    #888;
      --font-display:   'DM Serif Display', serif;
      --font-body:      'DM Sans', sans-serif;
      --max-width:      1100px;
      --radius:         12px;
    }

    /* =============================================
       RESET & BASE STYLES
       Browsers have their own default styles — this
       evens the playing field.
    ============================================= */
    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--color-bg);
      color: var(--color-text);
      font-family: var(--font-body);
      font-weight: 300;
      line-height: 1.7;
    }

    /* =============================================
       NAVIGATION
       <nav> is a semantic tag — it tells browsers
       this is site navigation, not just any links.
    ============================================= */
    nav {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.5rem 2rem;
      border-bottom: 1px solid #222;
    }

    .nav-logo {
      font-family: var(--font-display);
      font-size: 1.4rem;
      color: var(--color-accent);
      text-decoration: none;
    }

    .nav-links {
      list-style: none;      /* removes bullet points */
      display: flex;
      gap: 2rem;
    }

    .nav-links a {
      color: var(--color-muted);
      text-decoration: none;
      font-size: 0.9rem;
      letter-spacing: 0.05em;
      text-transform: uppercase;
    }

    /* =============================================
       HERO SECTION
       The big intro area at the top of the page.
    ============================================= */
    .hero {
      max-width: var(--max-width);
      margin: 0 auto;
      padding: 6rem 2rem 4rem;
    }

    .hero-label {
      color: var(--color-accent);
      font-size: 0.85rem;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      margin-bottom: 1rem;
    }

    .hero h1 {
      font-family: var(--font-display);
      font-size: clamp(2.5rem, 6vw, 5rem);  /* clamp = responsive font size */
      line-height: 1.1;
      margin-bottom: 1.5rem;
    }

    .hero h1 em {
      color: var(--color-accent);
      font-style: normal;
    }

    .hero-bio {
      max-width: 520px;
      color: var(--color-muted);
      font-size: 1.1rem;
      margin-bottom: 2.5rem;
    }

    .btn {
      display: inline-block;
      background: var(--color-accent);
      color: #0f0f0f;
      padding: 0.75rem 1.75rem;
      border-radius: 999px;
      text-decoration: none;
      font-weight: 500;
      font-size: 0.95rem;
    }

    /* =============================================
       ABOUT SECTION
       <section> groups related content together.
    ============================================= */
    .about {
      max-width: var(--max-width);
      margin: 0 auto;
      padding: 4rem 2rem;
      border-top: 1px solid #222;
    }

    .section-title {
      font-family: var(--font-display);
      font-size: 2rem;
      margin-bottom: 1.5rem;
    }

    .about p {
      max-width: 600px;
      color: var(--color-muted);
      font-size: 1.05rem;
    }

    /* =============================================
       PROJECTS SECTION
       Simple cards laid out in a row for now —
       in Stage 2 we'll use CSS Grid to make this
       look much better!
    ============================================= */
    .projects {
      max-width: var(--max-width);
      margin: 0 auto;
      padding: 4rem 2rem;
      border-top: 1px solid #222;
    }

    .project-list {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
      margin-top: 2rem;
    }

    .project-card {
      background: var(--color-surface);
      border: 1px solid #2a2a2a;
      border-radius: var(--radius);
      padding: 1.75rem;
      flex: 1 1 280px;         /* flex-grow, flex-shrink, min width */
    }

    .project-card h3 {
      font-family: var(--font-display);
      font-size: 1.3rem;
      margin-bottom: 0.5rem;
    }

    .project-card p {
      color: var(--color-muted);
      font-size: 0.95rem;
    }

    .project-tag {
      display: inline-block;
      background: #252525;
      color: var(--color-accent);
      font-size: 0.75rem;
      padding: 0.2rem 0.6rem;
      border-radius: 999px;
      margin-top: 1rem;
      margin-right: 0.25rem;
    }

    /* =============================================
       FOOTER
       <footer> is a semantic tag for page footer.
    ============================================= */
    footer {
      text-align: center;
      padding: 3rem 2rem;
      color: var(--color-muted);
      font-size: 0.85rem;
      border-top: 1px solid #222;
      margin-top: 4rem;
    }

  </style>
</head>

<body>

  <!-- NAVIGATION -->
  <nav>
    <a href="@" class="nav-logo" style="font-size: 30px;">rhurt</a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO SECTION -->
  <header class="hero">
    <p class="hero-label">👋 Hello, I'm</p>
    <h1>A developer who<br>loves <em>building things</em></h1>
    <p class="hero-bio">
      I'm a web developer with a passion for clean design and thoughtful experiences.
      Currently available for freelance work and collaborations.
    </p>
    <a href="#projects" class="btn">See my work</a>
  </header>

  <!-- ABOUT SECTION -->
  <section class="about" id="about">
    <h2 class="section-title">About me</h2>
    <p>
      I love turning ideas into real things on the internet. When I'm not coding,
      you'll find me hiking, reading, or tinkering with side projects. I believe
      great design is about solving problems beautifully.
    </p>
  </section>

  <!-- PROJECTS SECTION -->
  <section class="projects" id="projects">
    <h2 class="section-title">Projects</h2>
    <div class="project-list">

      <article class="project-card">
        <h3>Project One</h3>
        <p>A short description of what this project does and why it's interesting.</p>
        <span class="project-tag">HTML</span>
        <span class="project-tag">CSS</span>
      </article>

      <article class="project-card">
        <h3>Project Two</h3>
        <p>A short description of what this project does and why it's interesting.</p>
        <span class="project-tag">JavaScript</span>
        <span class="project-tag">API</span>
      </article>

      <article class="project-card">
        <h3>Project Three</h3>
        <p>A short description of what this project does and why it's interesting.</p>
        <span class="project-tag">Design</span>
        <span class="project-tag">CSS</span>
      </article>

    </div>
  </section>

  <!-- FOOTER -->
  <footer id="contact">
    <p>Built by YourName · <a href="mailto:you@email.com" style="color: var(--color-accent);">you@email.com</a></p>
  </footer>


</body></html>