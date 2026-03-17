<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>João Pedro Queiroz — Engenheiro de Dados</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #080c10;
    --bg2: #0d1117;
    --bg3: #111820;
    --accent: #00d4aa;
    --accent2: #0096ff;
    --text: #e8edf2;
    --muted: #6b7a8d;
    --border: rgba(255,255,255,0.07);
    --card: rgba(255,255,255,0.03);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* cursor */
  .cursor {
    width: 8px; height: 8px;
    background: var(--accent);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s;
    transform: translate(-50%, -50%);
  }
  .cursor-ring {
    width: 32px; height: 32px;
    border: 1px solid rgba(0,212,170,0.4);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: transform 0.15s, width 0.2s, height 0.2s, opacity 0.2s;
    transform: translate(-50%, -50%);
  }

  /* grid bg */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,170,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,170,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 20px 60px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(8,12,16,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-size: 15px;
    font-weight: 700;
    letter-spacing: 0.1em;
    color: var(--accent);
    font-family: 'JetBrains Mono', monospace;
  }

  .nav-links {
    display: flex;
    gap: 36px;
    list-style: none;
  }

  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 13px;
    font-weight: 500;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    transition: color 0.2s;
  }

  .nav-links a:hover { color: var(--accent); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 120px 60px 80px;
    position: relative;
    z-index: 1;
  }

  .hero-content { max-width: 800px; }

  .hero-tag {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.2s;
  }

  .hero-tag::before {
    content: '';
    width: 24px; height: 1px;
    background: var(--accent);
  }

  .hero h1 {
    font-size: clamp(52px, 7vw, 88px);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    margin-bottom: 24px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.4s;
  }

  .hero h1 span {
    display: block;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-desc {
    font-size: 17px;
    color: var(--muted);
    line-height: 1.7;
    max-width: 520px;
    margin-bottom: 48px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.6s;
  }

  .hero-actions {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.8s;
  }

  .btn-primary {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 14px 28px;
    background: var(--accent);
    color: #080c10;
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    font-weight: 700;
    text-decoration: none;
    letter-spacing: 0.05em;
    transition: all 0.2s;
    clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  }

  .btn-primary:hover {
    background: #fff;
    transform: translateY(-2px);
  }

  .btn-secondary {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 13px 27px;
    border: 1px solid var(--border);
    color: var(--muted);
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    font-weight: 500;
    text-decoration: none;
    letter-spacing: 0.05em;
    transition: all 0.2s;
  }

  .btn-secondary:hover {
    border-color: var(--accent);
    color: var(--accent);
    transform: translateY(-2px);
  }

  .hero-stats {
    position: absolute;
    right: 60px;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    flex-direction: column;
    gap: 32px;
    opacity: 0;
    animation: fadeLeft 0.6s ease forwards 1s;
  }

  .stat-item {
    text-align: right;
  }

  .stat-num {
    font-size: 36px;
    font-weight: 800;
    color: var(--accent);
    line-height: 1;
    font-family: 'JetBrains Mono', monospace;
  }

  .stat-label {
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-top: 4px;
  }

  /* SECTIONS */
  section {
    padding: 100px 60px;
    position: relative;
    z-index: 1;
  }

  .section-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 60px;
  }

  .section-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    letter-spacing: 0.1em;
  }

  .section-title {
    font-size: 36px;
    font-weight: 800;
    letter-spacing: -0.02em;
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* SOBRE */
  .sobre-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: start;
  }

  .sobre-text p {
    font-size: 16px;
    color: var(--muted);
    line-height: 1.8;
    margin-bottom: 20px;
  }

  .sobre-text p strong {
    color: var(--text);
    font-weight: 600;
  }

  .sobre-info {
    display: flex;
    flex-direction: column;
    gap: 16px;
  }

  .info-row {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 14px 18px;
    background: var(--card);
    border: 1px solid var(--border);
    font-size: 14px;
  }

  .info-row .info-label {
    color: var(--muted);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    min-width: 80px;
    font-family: 'JetBrains Mono', monospace;
  }

  .info-row .info-val {
    color: var(--text);
    font-weight: 500;
  }

  .info-row a {
    color: var(--accent);
    text-decoration: none;
  }

  /* SKILLS */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
  }

  .skill-card {
    padding: 28px;
    background: var(--card);
    border: 1px solid var(--border);
    transition: border-color 0.2s, transform 0.2s;
    position: relative;
    overflow: hidden;
  }

  .skill-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 0;
    background: var(--accent);
    transition: height 0.3s;
  }

  .skill-card:hover {
    border-color: rgba(0,212,170,0.3);
    transform: translateY(-4px);
  }

  .skill-card:hover::before { height: 100%; }

  .skill-cat {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    font-family: 'JetBrains Mono', monospace;
    margin-bottom: 16px;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .skill-tag {
    padding: 5px 12px;
    background: rgba(0,212,170,0.07);
    border: 1px solid rgba(0,212,170,0.15);
    color: var(--text);
    font-size: 13px;
    font-family: 'JetBrains Mono', monospace;
    font-weight: 400;
  }

  /* PROJETOS */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
    gap: 24px;
  }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    overflow: hidden;
    transition: all 0.3s;
    position: relative;
  }

  .project-card:hover {
    border-color: rgba(0,212,170,0.3);
    transform: translateY(-6px);
  }

  .project-top {
    padding: 28px 28px 0;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
  }

  .project-icon {
    width: 44px; height: 44px;
    background: rgba(0,212,170,0.1);
    border: 1px solid rgba(0,212,170,0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
  }

  .project-links {
    display: flex;
    gap: 10px;
  }

  .project-link {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 32px; height: 32px;
    border: 1px solid var(--border);
    color: var(--muted);
    text-decoration: none;
    font-size: 14px;
    transition: all 0.2s;
  }

  .project-link:hover {
    border-color: var(--accent);
    color: var(--accent);
  }

  .project-body { padding: 20px 28px 28px; }

  .project-name {
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 10px;
    letter-spacing: -0.01em;
  }

  .project-desc {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 20px;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .stack-tag {
    padding: 3px 10px;
    background: rgba(0,150,255,0.08);
    border: 1px solid rgba(0,150,255,0.15);
    color: #6bb8ff;
    font-size: 11px;
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 0.05em;
  }

  /* FORMAÇÃO */
  .edu-list {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .edu-card {
    display: grid;
    grid-template-columns: 120px 1fr;
    gap: 28px;
    padding: 28px;
    background: var(--card);
    border: 1px solid var(--border);
    transition: border-color 0.2s;
  }

  .edu-card:hover { border-color: rgba(0,212,170,0.3); }

  .edu-period {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.05em;
    line-height: 1.6;
    padding-top: 3px;
  }

  .edu-name {
    font-size: 16px;
    font-weight: 700;
    margin-bottom: 4px;
  }

  .edu-inst {
    font-size: 13px;
    color: var(--accent);
    margin-bottom: 10px;
    font-family: 'JetBrains Mono', monospace;
  }

  .edu-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.6;
  }

  /* CERTS */
  .certs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
  }

  .cert-card {
    padding: 24px;
    background: var(--card);
    border: 1px solid var(--border);
    transition: all 0.2s;
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }

  .cert-card:hover {
    border-color: rgba(0,212,170,0.3);
    transform: translateY(-3px);
  }

  .cert-badge {
    width: 40px; height: 40px;
    background: rgba(0,212,170,0.1);
    border: 1px solid rgba(0,212,170,0.2);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    flex-shrink: 0;
  }

  .cert-info {}

  .cert-name {
    font-size: 14px;
    font-weight: 600;
    margin-bottom: 4px;
    line-height: 1.4;
  }

  .cert-org {
    font-size: 12px;
    color: var(--accent);
    font-family: 'JetBrains Mono', monospace;
    margin-bottom: 4px;
  }

  .cert-meta {
    font-size: 11px;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
  }

  /* CONTATO */
  .contact-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 60px;
    align-items: start;
  }

  .contact-text h3 {
    font-size: 28px;
    font-weight: 800;
    margin-bottom: 16px;
    letter-spacing: -0.02em;
  }

  .contact-text p {
    font-size: 15px;
    color: var(--muted);
    line-height: 1.7;
    margin-bottom: 32px;
  }

  .contact-links {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .contact-link {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 16px 20px;
    background: var(--card);
    border: 1px solid var(--border);
    text-decoration: none;
    color: var(--text);
    font-size: 14px;
    transition: all 0.2s;
  }

  .contact-link:hover {
    border-color: var(--accent);
    color: var(--accent);
    transform: translateX(6px);
  }

  .contact-link-icon {
    font-size: 16px;
    width: 20px;
    text-align: center;
  }

  .contact-link-label {
    color: var(--muted);
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    font-family: 'JetBrains Mono', monospace;
    min-width: 60px;
  }

  .availability {
    padding: 28px;
    background: rgba(0,212,170,0.05);
    border: 1px solid rgba(0,212,170,0.15);
  }

  .avail-dot {
    display: inline-block;
    width: 8px; height: 8px;
    background: var(--accent);
    border-radius: 50%;
    margin-right: 8px;
    animation: pulse 2s ease-in-out infinite;
  }

  .avail-title {
    font-size: 14px;
    font-weight: 600;
    margin-bottom: 12px;
    color: var(--accent);
  }

  .avail-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.7;
  }

  /* FOOTER */
  footer {
    padding: 32px 60px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
    z-index: 1;
  }

  footer p {
    font-size: 12px;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
  }

  footer span { color: var(--accent); }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeLeft {
    from { opacity: 0; transform: translate(24px, -50%); }
    to { opacity: 1; transform: translate(0, -50%); }
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(1.3); }
  }

  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: rgba(0,212,170,0.3); border-radius: 2px; }

  @media (max-width: 768px) {
    nav { padding: 16px 24px; }
    .hero { padding: 100px 24px 60px; }
    .hero-stats { display: none; }
    section { padding: 60px 24px; }
    .sobre-grid, .contact-grid { grid-template-columns: 1fr; }
    .edu-card { grid-template-columns: 1fr; gap: 8px; }
    footer { padding: 24px; flex-direction: column; gap: 8px; text-align: center; }
    .nav-links { display: none; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<nav>
  <div class="nav-logo">queiroz.dev</div>
  <ul class="nav-links">
    <li><a href="#sobre">Sobre</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projetos">Projetos</a></li>
    <li><a href="#formacao">Formação</a></li>
    <li><a href="#contato">Contato</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="inicio">
  <div class="hero-content">
    <div class="hero-tag">Disponível para oportunidades</div>
    <h1>
      João Pedro<br>
      <span>Queiroz</span>
    </h1>
    <p class="hero-desc">
      Engenheiro de Dados e Desenvolvedor Backend Python
    </p>
    <div class="hero-actions">
      <a href="#projetos" class="btn-primary">Ver projetos →</a>
      <a href="#contato" class="btn-secondary">Entre em contato</a>
    </div>
  </div>

</section>

<!-- SOBRE -->
<section id="sobre">
  <div class="section-header reveal">
    <span class="section-num">01</span>
    <h2 class="section-title">Sobre mim</h2>
    <div class="section-line"></div>
  </div>
  <div class="sobre-grid">
    <div class="sobre-text reveal">
      <p>
        Estudante de <strong>Engenharia de dados</strong> e <strong>Desenvolvimento Backend</strong> na linguagem Python. Busco uma oportunidade para aplicar meus conhecimentos em projetos reais, contribuindo para o 
        desenvolvimento de soluções escaláveis e resolução de problemas orientado a dados
      </p>
      <p>
        Tenho experiência na construção de <strong>Projetos pessoais</strong>, presentes no meu Github. Tais projetos vão desde a lógica básica até
        <strong>APIs RESTful com FastAPI</strong>, orquestração com <strong>Airflow</strong>, containerização com <strong>Docker</strong>, uso do <strong>WSL</strong> entre outros.
      </p>
      <p>
        Busco oportunidade como <strong>estagiário ou desenvolvedor júnior</strong> para aplicar meus conhecimentos em projetos reais e aprender muito mais. Disponibilidade imediata para remoto, híbrido ou presencial em <strong>Brasília-DF</strong>
      </p>
    </div>
    <div class="sobre-info reveal">
      <div class="info-row">
        <span class="info-label">Local</span>
        <span class="info-val">Brasília - DF</span>
      </div>
      <div class="info-row">
        <span class="info-label">Foco</span>
        <span class="info-val">Engenharia de Dados · Backend</span>
      </div>
      <div class="info-row">
        <span class="info-label">Inglês</span>
        <span class="info-val">Formado — Pró-Línguas</span>
      </div>
      <div class="info-row">
        <span class="info-label">Email</span>
        <span class="info-val"><a href="mailto:jpqueiroz.work@gmail.com">jpqueiroz.work@gmail.com</a></span>
      </div>
      <div class="info-row">
        <span class="info-label">Regime</span>
        <span class="info-val">Remoto · Híbrido · Presencial</span>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" style="background: var(--bg2)">
  <div class="section-header reveal">
    <span class="section-num">02</span>
    <h2 class="section-title">Tecnologias</h2>
    <div class="section-line"></div>
  </div>
  <div class="skills-grid">
    <div class="skill-card reveal">
      <div class="skill-cat">Linguagens</div>
      <div class="skill-tags">
        <span class="skill-tag">Python</span>
        <span class="skill-tag">Java</span>
        <span class="skill-tag">SQL</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <div class="skill-cat">Backend & APIs</div>
      <div class="skill-tags">
        <span class="skill-tag">FastAPI</span>
        <span class="skill-tag">Flask</span>
        <span class="skill-tag">RESTful APIs</span>
        <span class="skill-tag">Postman</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <div class="skill-cat">Dados & ETL</div>
      <div class="skill-tags">
        <span class="skill-tag">ETL</span>
        <span class="skill-tag">ELT</span>
        <span class="skill-tag">Airflow</span>
        <span class="skill-tag">Pandas</span>
        <span class="skill-tag">Power BI</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <div class="skill-cat">Bancos de Dados</div>
      <div class="skill-tags">
        <span class="skill-tag">PostgreSQL</span>
        <span class="skill-tag">MySQL</span>
        <span class="skill-tag">SQLite</span>
        <span class="skill-tag">SQLAlchemy</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <div class="skill-cat">DevOps & Infra</div>
      <div class="skill-tags">
        <span class="skill-tag">Docker</span>
        <span class="skill-tag">Git</span>
        <span class="skill-tag">GitHub</span>
        <span class="skill-tag">WSL</span>
        <span class="skill-tag">Linux</span>
      </div>
    </div>
    <div class="skill-card reveal">
      <div class="skill-cat">Análise & BI</div>
      <div class="skill-tags">
        <span class="skill-tag">Excel</span>
        <span class="skill-tag">Power BI</span>
        <span class="skill-tag">Business Intelligence</span>
      </div>
    </div>
  </div>
</section>

<!-- PROJETOS -->
<section id="projetos">
  <div class="section-header reveal">
    <span class="section-num">03</span>
    <h2 class="section-title">Projetos</h2>
    <div class="section-line"></div>
  </div>
  <div class="projects-grid">

    <div class="project-card reveal">
      <div class="project-top">
        <div class="project-icon">⚙️</div>
        <div class="project-links">
          <a href="https://github.com/queiroz107911/Data_API" target="_blank" class="project-link" title="GitHub">⌥</a>
        </div>
      </div>
      <div class="project-body">
        <div class="project-name">Pipeline ETL de Funcionários</div>
        <div class="project-desc">Pipeline completo de ETL com dados fictícios de funcionários. Geração de CSV com erros propositais, tratamento e carga em banco de dados com API de consulta paginada.</div>
        <div class="project-stack">
          <span class="stack-tag">Python</span>
          <span class="stack-tag">FastAPI</span>
          <span class="stack-tag">PostgreSQL</span>
          <span class="stack-tag">Docker</span>
          <span class="stack-tag">Airflow</span>
          <span class="stack-tag">Pandas</span>
        </div>
      </div>
    </div>

    <div class="project-card reveal">
      <div class="project-top">
        <div class="project-icon">🛒</div>
        <div class="project-links">
          <a href="https://github.com/queiroz107911/Ecommerce-FastAPI" target="_blank" class="project-link" title="GitHub">⌥</a>
        </div>
      </div>
      <div class="project-body">
        <div class="project-name">Ecommerce API</div>
        <div class="project-desc">API REST de e-commerce com autenticação JWT, sistema de pedidos, controle de acesso por roles (admin/usuário) e gerenciamento de itens.</div>
        <div class="project-stack">
          <span class="stack-tag">Python</span>
          <span class="stack-tag">FastAPI</span>
          <span class="stack-tag">SQLAlchemy</span>
          <span class="stack-tag">JWT</span>
          <span class="stack-tag">Alembic</span>
          <span class="stack-tag">SQLite</span>
        </div>
      </div>
    </div>

    <div class="project-card reveal" style="border-style: dashed; opacity: 0.5;">
      <div class="project-top">
        <div class="project-icon">+</div>
      </div>
      <div class="project-body">
        <div class="project-name" style="color: var(--muted)">Novos projetos em breve</div>
        <div class="project-desc"></div>
      </div>
    </div>

  </div>
</section>

<!-- FORMAÇÃO -->
<section id="formacao" style="background: var(--bg2)">
  <div class="section-header reveal">
    <span class="section-num">04</span>
    <h2 class="section-title">Formação</h2>
    <div class="section-line"></div>
  </div>
  <div class="edu-list">
    <div class="edu-card reveal">
      <div class="edu-period">fev/2026<br>jul/2029</div>
      <div>
        <div class="edu-name">Ciência de Dados e Machine Learning</div>
        <div class="edu-inst">CEUB — Centro Universitário de Brasília</div>
        <div class="edu-desc">Banco de Dados · Business Intelligence · Big Data · DevOps · Deep Learning · IA</div>
      </div>
    </div>
    <div class="edu-card reveal">
      <div class="edu-period">2024<br>2026</div>
      <div>
        <div class="edu-name">Engenharia de Redes e Comunicação</div>
        <div class="edu-inst">UnB — Universidade de Brasília</div>
        <div class="edu-desc">Cálculo · Álgebra Linear · Estrutura de Dados · Probabilidade e Estatística · Teoria dos Grafos — Cursado até o 4° semestre</div>
      </div>
    </div>
    <div class="edu-card reveal">
      <div class="edu-period">concluído</div>
      <div>
        <div class="edu-name">Formação em Inglês</div>
        <div class="edu-inst">Pró-Línguas</div>
        <div class="edu-desc">Certificado de conclusão</div>
      </div>
    </div>
  </div>

  <div style="margin-top: 60px">
    <div class="section-header reveal">
      <span class="section-num">05</span>
      <h2 class="section-title">Certificados</h2>
      <div class="section-line"></div>
    </div>
    <div class="certs-grid">
      <div class="cert-card reveal">
        <div class="cert-badge">📊</div>
        <div class="cert-info">
          <div class="cert-name">Fundamentos de Engenharia de Dados</div>
          <div class="cert-org">Data Science Academy</div>
          <div class="cert-meta">24h · 97% aproveitamento · fev/2026</div>
        </div>
      </div>
      <div class="cert-card reveal">
        <div class="cert-badge">📈</div>
        <div class="cert-info">
          <div class="cert-name">Microsoft Power BI Para Business Intelligence e Data Science</div>
          <div class="cert-org">Data Science Academy</div>
          <div class="cert-meta">72h · 100% aproveitamento · mar/2026</div>
        </div>
      </div>
      <div class="cert-card reveal">
        <div class="cert-badge">🤖</div>
        <div class="cert-info">
          <div class="cert-name">Fundamentos de Data Science e Inteligência Artificial</div>
          <div class="cert-org">Data Science Academy</div>
          <div class="cert-meta">24h · 88% aproveitamento · dez/2025</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTATO -->
<section id="contato">
  <div class="section-header reveal">
    <span class="section-num">06</span>
    <h2 class="section-title">Contato</h2>
    <div class="section-line"></div>
  </div>
  <div class="contact-grid">
    <div class="contact-text reveal">
      <div class="contact-links">
        <a href="mailto:jpqueiroz.work@gmail.com" class="contact-link">
          <span class="contact-link-icon">✉</span>
          <span class="contact-link-label">Email</span>
          <span>jpqueiroz.work@gmail.com</span>
        </a>
        <a href="https://www.linkedin.com/in/qz-joao/" target="_blank" class="contact-link">
          <span class="contact-link-icon">in</span>
          <span class="contact-link-label">LinkedIn</span>
          <span>linkedin.com/in/qz-joao</span>
        </a>
        <a href="https://github.com/queiroz107911" target="_blank" class="contact-link">
          <span class="contact-link-icon">⌥</span>
          <span class="contact-link-label">GitHub</span>
          <span>github.com/queiroz107911</span>
        </a>
        <a href="tel:+5561998748156" class="contact-link">
          <span class="contact-link-icon">☏</span>
          <span class="contact-link-label">Telefone</span>
          <span>(61) 998748156</span>
        </a>
      </div>
    </div>
    <div class="reveal">
      <div class="availability">
        <div class="avail-title"><span class="avail-dot"></span>Disponível agora</div>
        <div class="avail-desc">
          Aberto a oportunidades como <strong style="color:var(--text)">estagiário ou desenvolvedor júnior</strong> nas áreas de Engenharia de Dados e Backend Python.<br><br>
          Modalidade: <strong style="color:var(--text)">remoto, híbrido ou presencial</strong> em Brasília-DF.<br><br>
          Início: <strong style="color:var(--accent)">imediato</strong>
        </div>
      </div>
    </div>
  </div>
</section>

<footer>
  <p>© 2026 <span>João Pedro Queiroz</span> — Engenheiro de Dados</p>
</footer>

<script>
  // cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });
  function animRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, button').forEach(el => {
    el.addEventListener('mouseenter', () => {
      ring.style.width = '48px';
      ring.style.height = '48px';
      ring.style.opacity = '0.6';
    });
    el.addEventListener('mouseleave', () => {
      ring.style.width = '32px';
      ring.style.height = '32px';
      ring.style.opacity = '1';
    });
  });

  // scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 80);
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
