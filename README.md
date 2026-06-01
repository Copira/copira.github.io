<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>United AI — Intelligent Travel</title>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@300;400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --united-blue: #003580;
    --united-mid: #1a5fab;
    --united-sky: #4a9fd4;
    --united-light: #e8f2fa;
    --gold: #c8922a;
    --gold-light: #f5e6c8;
    --white: #ffffff;
    --off-white: #f7f9fc;
    --text-primary: #0a1628;
    --text-secondary: #4a5568;
    --text-muted: #8a9ab0;
    --border: #d1dcea;
    --radius: 12px;
    --radius-lg: 20px;
    --shadow: 0 4px 24px rgba(0,53,128,0.08);
    --shadow-hover: 0 8px 40px rgba(0,53,128,0.16);
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body { font-family: 'Sora', sans-serif; background: var(--off-white); color: var(--text-primary); min-height: 100vh; }

  nav {
    background: var(--united-blue); padding: 0 48px;
    display: flex; align-items: center; justify-content: space-between;
    height: 64px; position: sticky; top: 0; z-index: 100;
    border-bottom: 2px solid rgba(255,255,255,0.08);
  }
  .nav-logo { display: flex; align-items: center; gap: 12px; text-decoration: none; cursor: pointer; }
  .nav-logo-globe {
    width: 36px; height: 36px; border: 2px solid var(--gold); border-radius: 50%;
    display: flex; align-items: center; justify-content: center; position: relative; overflow: hidden;
  }
  .nav-logo-globe::before { content:''; position:absolute; width:100%; height:1px; background:var(--gold); top:50%; }
  .nav-logo-globe::after { content:''; position:absolute; height:100%; width:1px; background:var(--gold); left:50%; }
  .nav-wordmark { font-size: 18px; font-weight: 600; color: white; letter-spacing: -0.3px; }
  .nav-wordmark span { color: var(--gold); }
  .nav-links { display: flex; gap: 32px; list-style: none; }
  .nav-links a { color: rgba(255,255,255,0.75); text-decoration: none; font-size: 13px; font-weight: 500; letter-spacing: 0.3px; transition: color 0.2s; }
  .nav-links a:hover { color: white; }
  .nav-cta { background: var(--gold); color: var(--united-blue) !important; padding: 8px 18px; border-radius: 100px; font-weight: 600 !important; }

  .hero {
    background: linear-gradient(135deg, var(--united-blue) 0%, #0f4090 50%, #1a5fab 100%);
    padding: 80px 48px 72px; position: relative; overflow: hidden;
  }
  .hero::before { content:''; position:absolute; right:-100px; top:-100px; width:600px; height:600px; border:1px solid rgba(255,255,255,0.05); border-radius:50%; }
  .hero-inner { max-width: 1200px; margin: 0 auto; position: relative; z-index: 1; }
  .hero-eyebrow {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(200,146,42,0.2); border: 1px solid rgba(200,146,42,0.4);
    color: var(--gold-light); padding: 6px 14px; border-radius: 100px;
    font-size: 12px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase; margin-bottom: 24px;
  }
  .hero-eyebrow::before { content:''; width:6px; height:6px; background:var(--gold); border-radius:50%; }
  .hero h1 { font-size: 52px; font-weight: 700; color: white; line-height: 1.1; letter-spacing: -1.5px; margin-bottom: 20px; max-width: 640px; }
  .hero h1 em { font-style: normal; color: var(--gold); }
  .hero p { font-size: 17px; color: rgba(255,255,255,0.7); max-width: 540px; line-height: 1.7; margin-bottom: 40px; }

  .main-content { max-width: 1200px; margin: 0 auto; padding: 56px 48px; }
  .section-header { display: flex; align-items: baseline; justify-content: space-between; margin-bottom: 32px; }
  .section-header h2 { font-size: 24px; font-weight: 600; letter-spacing: -0.5px; }
  .section-header span { font-size: 13px; color: var(--text-muted); font-family: 'IBM Plex Mono', monospace; }

  .tool-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; margin-bottom: 64px; }
  .tool-card {
    background: white; border-radius: var(--radius-lg); border: 1px solid var(--border);
    padding: 28px; text-decoration: none; color: inherit; display: block;
    transition: all 0.25s; position: relative; overflow: hidden; cursor: pointer;
  }
  .tool-card:hover { border-color: var(--united-sky); box-shadow: var(--shadow-hover); transform: translateY(-2px); }
  .tool-card.featured { border-color: var(--gold); background: linear-gradient(135deg, #fffdf5 0%, white 100%); }
  .tool-card.featured::before {
    content: '★ BCG STAR'; position: absolute; top: 16px; right: 16px;
    font-size: 10px; font-weight: 600; letter-spacing: 0.8px; color: var(--gold);
    background: var(--gold-light); padding: 3px 8px; border-radius: 100px; font-family: 'IBM Plex Mono', monospace;
  }
  .tool-card.soon { opacity: 0.55; cursor: default; }
  .tool-card.soon::after {
    content: 'COMING SOON'; position: absolute; top: 16px; right: 16px;
    font-size: 10px; font-weight: 600; letter-spacing: 0.8px; color: var(--text-muted);
    background: var(--off-white); padding: 3px 8px; border-radius: 100px; font-family: 'IBM Plex Mono', monospace;
  }
  .tool-icon { width: 48px; height: 48px; border-radius: 12px; display: flex; align-items: center; justify-content: center; font-size: 22px; margin-bottom: 20px; }
  .tool-icon.blue { background: var(--united-light); }
  .tool-icon.gold { background: var(--gold-light); }
  .tool-icon.green { background: #e8f5ee; }
  .tool-icon.red { background: #fef0f0; }
  .tool-card h3 { font-size: 16px; font-weight: 600; margin-bottom: 8px; letter-spacing: -0.2px; }
  .tool-card p { font-size: 13px; color: var(--text-secondary); line-height: 1.6; }
  .tool-card .markets { margin-top: 16px; display: flex; gap: 6px; flex-wrap: wrap; }
  .market-tag { font-size: 11px; font-weight: 500; padding: 3px 8px; border-radius: 100px; background: var(--united-light); color: var(--united-mid); font-family: 'IBM Plex Mono', monospace; }
  .market-tag.gold-tag { background: var(--gold-light); color: #7a5010; }

  #planner-page { display: none; }
  .planner-header {
    background: var(--united-blue); padding: 0 48px; height: 56px;
    display: flex; align-items: center; gap: 16px; border-bottom: 1px solid rgba(255,255,255,0.1);
  }
  .back-btn {
    background: none; border: 1px solid rgba(255,255,255,0.25); color: rgba(255,255,255,0.8);
    padding: 6px 14px; border-radius: 100px; font-size: 12px; cursor: pointer;
    font-family: 'Sora', sans-serif; font-weight: 500; transition: all 0.2s;
  }
  .back-btn:hover { background: rgba(255,255,255,0.1); color: white; }
  .planner-header-title { font-size: 14px; font-weight: 500; color: rgba(255,255,255,0.85); }
  .planner-header-badge {
    margin-left: auto; font-size: 11px; font-weight: 600; letter-spacing: 0.8px;
    color: var(--gold); background: rgba(200,146,42,0.15); border: 1px solid rgba(200,146,42,0.3);
    padding: 3px 10px; border-radius: 100px; font-family: 'IBM Plex Mono', monospace;
  }

  .planner-body { max-width: 860px; margin: 0 auto; padding: 48px 24px; }
  .planner-title-row { margin-bottom: 36px; }
  .planner-title-row h2 { font-size: 30px; font-weight: 700; letter-spacing: -0.8px; margin-bottom: 8px; }
  .planner-title-row p { font-size: 14px; color: var(--text-secondary); line-height: 1.6; }

  .form-section { background: white; border-radius: var(--radius-lg); border: 1px solid var(--border); padding: 32px; margin-bottom: 20px; }
  .form-section-label {
    font-size: 11px; font-weight: 600; letter-spacing: 1.2px; color: var(--text-muted);
    text-transform: uppercase; font-family: 'IBM Plex Mono', monospace; margin-bottom: 20px;
    display: flex; align-items: center; gap: 10px;
  }
  .form-section-label::after { content:''; flex:1; height:1px; background:var(--border); }

  .journey-textarea {
    width: 100%; border: 1.5px solid var(--border); border-radius: 12px;
    padding: 16px 18px; font-family: 'Sora', sans-serif; font-size: 14px; line-height: 1.7;
    color: var(--text-primary); resize: vertical; min-height: 120px; transition: border-color 0.2s; background: var(--off-white);
  }
  .journey-textarea:focus { outline: none; border-color: var(--united-sky); background: white; }
  .journey-textarea::placeholder { color: var(--text-muted); }

  .route-row { display: grid; grid-template-columns: 1fr auto 1fr; gap: 12px; align-items: center; margin-bottom: 20px; }
  .route-input {
    border: 1.5px solid var(--border); border-radius: 10px; padding: 12px 16px;
    font-family: 'Sora', sans-serif; font-size: 14px; font-weight: 500; color: var(--text-primary);
    background: var(--off-white); transition: border-color 0.2s; width: 100%;
  }
  .route-input:focus { outline: none; border-color: var(--united-sky); background: white; }
  .route-arrow { font-size: 18px; color: var(--text-muted); text-align: center; }
  .date-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }

  .toggles-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 10px; }
  .toggle-item {
    display: flex; align-items: center; gap: 10px; padding: 12px 16px;
    border: 1.5px solid var(--border); border-radius: 10px; cursor: pointer;
    transition: all 0.2s; user-select: none; background: var(--off-white);
  }
  .toggle-item:hover { border-color: var(--united-sky); }
  .toggle-item.active { border-color: var(--united-mid); background: var(--united-light); }
  .toggle-check {
    width: 18px; height: 18px; border: 2px solid var(--border); border-radius: 5px;
    display: flex; align-items: center; justify-content: center; flex-shrink: 0; transition: all 0.2s;
  }
  .toggle-item.active .toggle-check { background: var(--united-mid); border-color: var(--united-mid); }
  .toggle-check-icon { display: none; font-size: 11px; font-weight: 700; color: white; }
  .toggle-item.active .toggle-check-icon { display: block; }
  .toggle-text { font-size: 13px; font-weight: 500; }
  .toggle-sub { font-size: 11px; color: var(--text-muted); display: block; }

  .go-row { display: flex; align-items: center; gap: 16px; margin-top: 24px; }
  .go-btn {
    background: var(--united-blue); color: white; border: none; padding: 16px 48px;
    border-radius: 100px; font-family: 'Sora', sans-serif; font-size: 16px; font-weight: 700;
    letter-spacing: 0.5px; cursor: pointer; transition: all 0.25s; display: flex; align-items: center; gap: 10px;
  }
  .go-btn:hover { background: var(--united-mid); transform: scale(1.02); }
  .go-btn:active { transform: scale(0.98); }
  .go-note { font-size: 12px; color: var(--text-muted); font-style: italic; }

  #loading-state { display: none; text-align: center; padding: 48px 24px; background: white; border-radius: var(--radius-lg); border: 1px solid var(--border); margin-top: 24px; }
  .loading-spinner { width: 40px; height: 40px; border: 3px solid var(--border); border-top-color: var(--united-blue); border-radius: 50%; margin: 0 auto 20px; animation: spin 0.8s linear infinite; }
  @keyframes spin { to { transform: rotate(360deg); } }
  .loading-steps { list-style: none; display: inline-flex; flex-direction: column; gap: 8px; text-align: left; margin-top: 16px; }
  .loading-step { font-size: 13px; color: var(--text-muted); display: flex; align-items: center; gap: 8px; font-family: 'IBM Plex Mono', monospace; }
  .loading-step.done { color: #2a8a4e; }
  .loading-step.active { color: var(--united-blue); font-weight: 500; }
  .step-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--border); flex-shrink: 0; transition: background 0.3s; }
  .loading-step.done .step-dot { background: #2a8a4e; }
  .loading-step.active .step-dot { background: var(--united-blue); animation: pulse 0.8s ease-in-out infinite; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.4} }

  #results-section { display: none; }
  .results-header { display: flex; align-items: baseline; justify-content: space-between; margin: 36px 0 20px; }
  .results-header h3 { font-size: 20px; font-weight: 600; letter-spacing: -0.4px; }
  .results-header span { font-size: 12px; color: var(--text-muted); font-family: 'IBM Plex Mono', monospace; }
  .results-explainer { background: var(--united-light); border-left: 3px solid var(--united-sky); padding: 14px 18px; border-radius: 0 10px 10px 0; font-size: 13px; color: var(--text-secondary); margin-bottom: 24px; line-height: 1.6; }

  .flight-cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin-bottom: 24px; }
  @media (max-width: 768px) { .flight-cards { grid-template-columns: 1fr; } }

  .flight-card { background: white; border: 1.5px solid var(--border); border-radius: var(--radius-lg); overflow: hidden; transition: all 0.25s; }
  .flight-card:hover { box-shadow: var(--shadow-hover); transform: translateY(-3px); }
  .flight-card.safe { border-color: #2a8a4e; }
  .flight-card.balanced { border-color: var(--united-sky); }
  .flight-card.risky { border-color: var(--gold); }

  .fc-header { padding: 16px 18px 14px; border-bottom: 1px solid var(--border); }
  .fc-tag { font-size: 10px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase; font-family: 'IBM Plex Mono', monospace; padding: 4px 10px; border-radius: 100px; display: inline-block; margin-bottom: 10px; }
  .safe .fc-tag { background: #e8f5ee; color: #1a6a35; }
  .balanced .fc-tag { background: var(--united-light); color: var(--united-mid); }
  .risky .fc-tag { background: var(--gold-light); color: #7a5010; }
  .fc-flight-number { font-size: 22px; font-weight: 700; letter-spacing: -0.5px; margin-bottom: 2px; }
  .fc-route { font-size: 12px; color: var(--text-muted); font-family: 'IBM Plex Mono', monospace; }

  .fc-times { padding: 16px 18px; display: flex; align-items: center; gap: 8px; border-bottom: 1px solid var(--border); }
  .fc-time-block { flex: 1; }
  .fc-time { font-size: 20px; font-weight: 600; letter-spacing: -0.5px; }
  .fc-airport { font-size: 11px; color: var(--text-muted); font-family: 'IBM Plex Mono', monospace; }
  .fc-duration { text-align: center; font-size: 11px; color: var(--text-muted); font-family: 'IBM Plex Mono', monospace; }
  .fc-dur-line { height: 1px; background: var(--border); width: 40px; margin: 4px auto; position: relative; }
  .fc-dur-line::after { content:'▶'; position:absolute; right:-4px; top:-6px; font-size:8px; color:var(--text-muted); }

  .fc-factors { padding: 14px 18px; display: flex; flex-direction: column; gap: 8px; }
  .fc-factor { display: flex; align-items: center; justify-content: space-between; font-size: 12px; }
  .fc-factor-label { color: var(--text-secondary); display: flex; align-items: center; gap: 6px; }
  .fc-factor-val { font-weight: 600; font-family: 'IBM Plex Mono', monospace; font-size: 11px; }
  .val-green { color: #1a6a35; }
  .val-amber { color: #7a5010; }
  .val-blue { color: var(--united-mid); }

  .fc-score { padding: 12px 18px; background: var(--off-white); display: flex; align-items: center; justify-content: space-between; border-top: 1px solid var(--border); }
  .fc-score-label { font-size: 11px; color: var(--text-muted); font-family: 'IBM Plex Mono', monospace; }
  .fc-score-bar { flex: 1; height: 4px; background: var(--border); border-radius: 100px; margin: 0 12px; overflow: hidden; }
  .fc-score-fill { height: 100%; border-radius: 100px; }
  .safe .fc-score-fill { background: #2a8a4e; }
  .balanced .fc-score-fill { background: var(--united-sky); }
  .risky .fc-score-fill { background: var(--gold); }

  .book-btn {
    display: block; width: calc(100% - 36px); margin: 14px 18px; padding: 12px;
    text-align: center; border-radius: 100px; border: 2px solid;
    font-family: 'Sora', sans-serif; font-size: 13px; font-weight: 600; cursor: pointer; transition: all 0.2s; text-decoration: none;
  }
  .safe .book-btn { border-color: #2a8a4e; color: #1a6a35; }
  .safe .book-btn:hover { background: #2a8a4e; color: white; }
  .balanced .book-btn { border-color: var(--united-mid); color: var(--united-mid); }
  .balanced .book-btn:hover { background: var(--united-mid); color: white; }
  .risky .book-btn { border-color: var(--gold); color: #7a5010; }
  .risky .book-btn:hover { background: var(--gold); color: white; }

  .ai-reasoning { background: white; border-radius: var(--radius-lg); border: 1px solid var(--border); padding: 24px 28px; margin-top: 20px; }
  .ai-reasoning-header { display: flex; align-items: center; gap: 10px; margin-bottom: 16px; }
  .ai-dot { width: 10px; height: 10px; background: var(--united-blue); border-radius: 50%; animation: pulse 1.5s ease-in-out infinite; }
  .ai-reasoning-header span { font-size: 13px; font-weight: 600; font-family: 'IBM Plex Mono', monospace; color: var(--united-blue); letter-spacing: 0.5px; }
  .ai-reasoning p { font-size: 14px; color: var(--text-secondary); line-height: 1.8; }

  footer { background: var(--united-blue); color: rgba(255,255,255,0.5); text-align: center; padding: 24px; font-size: 12px; margin-top: 80px; font-family: 'IBM Plex Mono', monospace; }
</style>
</head>
<body>

<!-- HOME PAGE -->
<div id="home-page">
  <nav>
    <div class="nav-logo" onclick="showHome()">
      <div class="nav-logo-globe"></div>
      <span class="nav-wordmark">United <span>AI</span></span>
    </div>
    <ul class="nav-links">
      <li><a href="#">Platform</a></li>
      <li><a href="#">Markets</a></li>
      <li><a href="#">Analytics</a></li>
      <li><a href="#">Team</a></li>
      <li><a href="#" class="nav-cta">Sign In</a></li>
    </ul>
  </nav>
  <div class="hero">
    <div class="hero-inner">
      <div class="hero-eyebrow">Intelligence Platform — Internal</div>
      <h1>Smart tools for smarter <em>air travel</em></h1>
      <p>AI-powered decision support across planning, operations, and passenger experience. Built for United's highest-value routes and travelers.</p>
    </div>
  </div>
  <div class="main-content">
    <div class="section-header">
      <h2>AI Tools</h2>
      <span>6 MODULES · 1 ACTIVE</span>
    </div>
    <div class="tool-grid">
      <div class="tool-card featured" onclick="showPlanner()" style="grid-column: span 2;">
        <div class="tool-icon gold">✈️</div>
        <h3>Business Travel Planner</h3>
        <p>AI-optimized flight selection for business travelers on high-demand routes. Compares transit times, TSA wait estimates, and on-time data to recommend the three best options for your journey.</p>
        <div class="markets">
          <span class="market-tag gold-tag">ORD · Chicago</span>
          <span class="market-tag gold-tag">LGA · LaGuardia</span>
          <span class="market-tag gold-tag">EWR · Newark</span>
        </div>
      </div>
      <div class="tool-card soon">
        <div class="tool-icon blue">📊</div>
        <h3>Revenue Yield Optimizer</h3>
        <p>Dynamic pricing recommendations by route, load factor, and competitor positioning.</p>
        <div class="markets"><span class="market-tag">All routes</span></div>
      </div>
      <div class="tool-card soon">
        <div class="tool-icon green">🔄</div>
        <h3>Connection Risk Analyzer</h3>
        <p>Predicts misconnect probability for itineraries based on gate distance, delay history, and buffer time.</p>
        <div class="markets"><span class="market-tag">ORD hub</span><span class="market-tag">IAH hub</span></div>
      </div>
      <div class="tool-card soon">
        <div class="tool-icon blue">🗺️</div>
        <h3>Lounge Traffic Forecast</h3>
        <p>Predicts United Club demand by terminal and time window to optimize staffing and catering.</p>
        <div class="markets"><span class="market-tag">Polaris</span><span class="market-tag">United Club</span></div>
      </div>
      <div class="tool-card soon">
        <div class="tool-icon red">⚡</div>
        <h3>IROPS Response AI</h3>
        <p>Automated rebooking priority and passenger communication during irregular operations.</p>
        <div class="markets"><span class="market-tag">Systemwide</span></div>
      </div>
      <div class="tool-card soon">
        <div class="tool-icon green">🌿</div>
        <h3>SAF Route Planner</h3>
        <p>Sustainable aviation fuel routing recommendations for corporate clients with carbon commitments.</p>
        <div class="markets"><span class="market-tag">Corporate</span></div>
      </div>
    </div>
  </div>
  <footer>UNITED AIRLINES — AI PLATFORM — INTERNAL USE ONLY — © 2025</footer>
</div>

<!-- PLANNER PAGE -->
<div id="planner-page">
  <nav>
    <div class="nav-logo" onclick="showHome()">
      <div class="nav-logo-globe"></div>
      <span class="nav-wordmark">United <span>AI</span></span>
    </div>
    <ul class="nav-links">
      <li><a href="#">Platform</a></li>
      <li><a href="#">Markets</a></li>
    </ul>
  </nav>
  <div class="planner-header">
    <button class="back-btn" onclick="showHome()">← Back</button>
    <span class="planner-header-title">Business Travel Planner · ORD / LGA / EWR</span>
    <span class="planner-header-badge">★ BCG STAR PRODUCT</span>
  </div>
  <div class="planner-body">
    <div class="planner-title-row">
      <h2>Plan your business trip</h2>
      <p>Describe your journey and preferences — our AI will compare flight options across transit time, TSA wait estimates, and reliability to find your best match.</p>
    </div>

    <div class="form-section">
      <div class="form-section-label">Journey description</div>
      <textarea class="journey-textarea" id="journey-text" placeholder="e.g. I'm Joe G, flying from LaGuardia to Chicago O'Hare tomorrow morning. I have a 10am meeting in the Loop and need to arrive by 9am.">I'm Joe G. I'm flying from LaGuardia to Chicago O'Hare tomorrow morning for a 9:30am client meeting in the Loop. I need to be downtown no later than 9am and prefer an aisle seat.</textarea>
    </div>

    <div class="form-section">
      <div class="form-section-label">Route & timing</div>
      <div class="route-row">
        <input type="text" class="route-input" id="origin" placeholder="Origin (e.g. LGA, EWR, JFK)" value="LGA" />
        <div class="route-arrow">→</div>
        <input type="text" class="route-input" id="destination" placeholder="Destination (e.g. ORD, MDW)" value="ORD" />
      </div>
      <div class="date-row">
        <input type="text" class="route-input" id="travel-date" placeholder="Travel date" value="Tomorrow" />
        <input type="text" class="route-input" id="must-arrive" placeholder="Must arrive by" value="9:00 AM" />
      </div>
    </div>

    <div class="form-section">
      <div class="form-section-label">Your options & preferences</div>
      <div class="toggles-grid">
        <label class="toggle-item active" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">TSA Precheck</span><span class="toggle-sub">Expedited security</span></div>
        </label>
        <label class="toggle-item" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">CLEAR</span><span class="toggle-sub">Biometric ID</span></div>
        </label>
        <label class="toggle-item" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">Global Entry</span><span class="toggle-sub">Intl arrivals</span></div>
        </label>
        <label class="toggle-item active" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">MileagePlus</span><span class="toggle-sub">United status</span></div>
        </label>
        <label class="toggle-item" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">Wheelchair</span><span class="toggle-sub">Accessibility needed</span></div>
        </label>
        <label class="toggle-item" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">Lounge Access</span><span class="toggle-sub">United Club</span></div>
        </label>
        <label class="toggle-item" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">Checked Bag</span><span class="toggle-sub">Extra check-in time</span></div>
        </label>
        <label class="toggle-item" onclick="toggleItem(this)">
          <div class="toggle-check"><span class="toggle-check-icon">✓</span></div>
          <div><span class="toggle-text">Express Transit</span><span class="toggle-sub">AirTrain / L train</span></div>
        </label>
      </div>
    </div>

    <div class="go-row">
      <button class="go-btn" onclick="runAI()">GO <span>→</span></button>
      <span class="go-note">AI compares TSA wait times, transit options & on-time data</span>
    </div>

    <div id="loading-state">
      <div class="loading-spinner"></div>
      <div style="font-size:14px; font-weight:600; color:var(--united-blue);">Analyzing your journey…</div>
      <ul class="loading-steps">
        <li class="loading-step" id="step1"><span class="step-dot"></span>Reading journey details</li>
        <li class="loading-step" id="step2"><span class="step-dot"></span>Fetching relevant flights</li>
        <li class="loading-step" id="step3"><span class="step-dot"></span>Estimating TSA wait times</li>
        <li class="loading-step" id="step4"><span class="step-dot"></span>Analyzing transit to downtown</li>
        <li class="loading-step" id="step5"><span class="step-dot"></span>Ranking options by risk &amp; time</li>
        <li class="loading-step" id="step6"><span class="step-dot"></span>Generating recommendations</li>
      </ul>
    </div>

    <div id="results-section"></div>
  </div>
  <footer>UNITED AIRLINES — AI PLATFORM — INTERNAL USE ONLY — © 2025</footer>
</div>

<script>
function showPlanner() {
  document.getElementById('home-page').style.display = 'none';
  document.getElementById('planner-page').style.display = 'block';
  window.scrollTo(0,0);
}
function showHome() {
  document.getElementById('planner-page').style.display = 'none';
  document.getElementById('home-page').style.display = 'block';
  document.getElementById('results-section').innerHTML = '';
  document.getElementById('results-section').style.display = 'none';
  document.getElementById('loading-state').style.display = 'none';
  window.scrollTo(0,0);
}
function toggleItem(el) { el.classList.toggle('active'); }
function getActiveToggles() {
  return Array.from(document.querySelectorAll('.toggle-item.active .toggle-text')).map(i => i.textContent);
}

// ── MOCK DATA ENGINE ──────────────────────────────────────────────────────────
// Generates realistic mock results based on the user's actual form inputs.
// No API call needed — works offline and on any static host.

function buildMockResults(origin, dest, date, arriveBy, toggles) {
  const hasTSA = toggles.includes('TSA Precheck');
  const hasCLEAR = toggles.includes('CLEAR');
  const hasWheelchair = toggles.includes('Wheelchair');

  const tsaFast = hasCLEAR ? '3–5 min (CLEAR)' : hasTSA ? '6–10 min (PreCheck)' : '22–35 min';
  const tsaMed  = hasCLEAR ? '3–5 min (CLEAR)' : hasTSA ? '8–12 min (PreCheck)' : '18–28 min';
  const tsaColor = (hasCLEAR || hasTSA) ? 'val-green' : 'val-amber';

  // Derive origin/dest labels
  const o = (origin || 'LGA').toUpperCase().trim();
  const d = (dest   || 'ORD').toUpperCase().trim();

  // Transit lookup by destination
  const transitMap = {
    ORD: { rail: 'Blue Line → Loop: ~45 min', taxi: 'Rideshare to Loop: ~30 min' },
    MDW: { rail: 'Orange Line → Loop: ~30 min', taxi: 'Rideshare to Loop: ~25 min' },
    LGA: { rail: 'AirTrain + E/M: ~55 min', taxi: 'Rideshare to Midtown: ~35 min' },
    EWR: { rail: 'NJ Transit → Penn: ~30 min', taxi: 'Rideshare to Midtown: ~45 min' },
    JFK: { rail: 'AirTrain + A: ~60 min', taxi: 'Rideshare to Midtown: ~50 min' },
    SFO: { rail: 'BART to Downtown: ~30 min', taxi: 'Rideshare to SOMA: ~25 min' },
    LAX: { rail: 'FlyAway Bus: ~45 min', taxi: 'Rideshare to DTLA: ~35 min' },
  };
  const transit = transitMap[d] || { rail: `Rail to downtown: ~40 min`, taxi: `Rideshare: ~30 min` };
  const transitLabel = transit.rail;

  // Wheelchair note
  const accessNote = hasWheelchair ? ' · Wheelchair assist pre-arranged at gate' : '';

  return {
    travelerName: extractName(document.getElementById('journey-text').value) || 'Traveler',
    routeSummary: `${o} → ${d}`,
    explainer: `Based on your ${date || 'tomorrow'} trip from ${o} to ${d}, the AI compared departure windows, current TSA wait estimates${hasTSA||hasCLEAR?' (expedited lane)':''}, and downtown transit options to find your best three flights.`,
    flights: [
      {
        type: 'risky',
        typeLabel: 'Fastest / Riskiest',
        flightNumber: `UA ${randFlight()}`,
        aircraft: 'B737-800',
        depTime: '5:55 AM',
        arrTime: '7:31 AM',
        depAirport: o,
        arrAirport: d,
        duration: '2h 36m',
        tsaWait: tsaFast,
        tsaColor: tsaColor,
        transitOption: transitLabel + accessNote,
        onTimePercent: '74%',
        onTimeColor: 'val-amber',
        bufferTime: '~14 min',
        price: '$219',
        confidence: 58,
        riskNote: '⚠ Very tight — any delay puts your meeting at risk'
      },
      {
        type: 'balanced',
        typeLabel: 'Best Balance',
        flightNumber: `UA ${randFlight()}`,
        aircraft: 'A320',
        depTime: '6:45 AM',
        arrTime: '8:22 AM',
        depAirport: o,
        arrAirport: d,
        duration: '2h 37m',
        tsaWait: tsaMed,
        tsaColor: tsaColor,
        transitOption: transitLabel + accessNote,
        onTimePercent: '88%',
        onTimeColor: 'val-green',
        bufferTime: '~38 min',
        price: '$259',
        confidence: 84,
        riskNote: null
      },
      {
        type: 'safe',
        typeLabel: 'Safest',
        flightNumber: `UA ${randFlight()}`,
        aircraft: 'B737 MAX 9',
        depTime: '5:10 AM',
        arrTime: '6:47 AM',
        depAirport: o,
        arrAirport: d,
        duration: '2h 37m',
        tsaWait: tsaFast,
        tsaColor: tsaColor,
        transitOption: transitLabel + accessNote,
        onTimePercent: '91%',
        onTimeColor: 'val-green',
        bufferTime: '~73 min',
        price: '$299',
        confidence: 95,
        riskNote: null
      }
    ],
    aiReasoning: `Given Joe G's hard 9:00 AM arrival constraint and ${hasTSA||hasCLEAR?'expedited security access':'standard security lanes'}, the <strong>Best Balance (UA ${randFlight()})</strong> is the recommended choice — it lands at ${d} by 8:22 AM, leaving a comfortable 38-minute buffer to reach downtown via the ${transit.rail.split(':')[0]} before the meeting. The 5:55 AM departure is technically feasible but its 74% on-time rate makes it a gamble. The 5:10 AM option provides the most cushion but requires an early wake for minimal additional benefit given the reliable 6:45 AM schedule.`
  };
}

function randFlight() {
  return String(Math.floor(Math.random() * 8000) + 1000);
}

function extractName(text) {
  const m = text.match(/(?:i['']m|my name is|named?)\s+([A-Z][a-z]+(?:\s+[A-Z]\.?)?)/i);
  return m ? m[1] : null;
}

// ── ANIMATION + RENDER ────────────────────────────────────────────────────────

function runAI() {
  const origin   = document.getElementById('origin').value;
  const dest     = document.getElementById('destination').value;
  const date     = document.getElementById('travel-date').value;
  const arriveBy = document.getElementById('must-arrive').value;
  const toggles  = getActiveToggles();

  document.getElementById('results-section').style.display = 'none';
  document.getElementById('results-section').innerHTML = '';
  const loadingEl = document.getElementById('loading-state');
  loadingEl.style.display = 'block';

  const steps = ['step1','step2','step3','step4','step5','step6'];
  steps.forEach(s => document.getElementById(s).className = 'loading-step');

  let idx = 0;
  function advance() {
    if (idx > 0) document.getElementById(steps[idx-1]).className = 'loading-step done';
    if (idx < steps.length) { document.getElementById(steps[idx]).className = 'loading-step active'; idx++; }
  }
  advance();
  const iv = setInterval(advance, 650);

  // Simulate analysis delay then show results
  setTimeout(() => {
    clearInterval(iv);
    steps.forEach(s => document.getElementById(s).className = 'loading-step done');
    setTimeout(() => {
      loadingEl.style.display = 'none';
      const data = buildMockResults(origin, dest, date, arriveBy, toggles);
      renderResults(data);
    }, 400);
  }, 4200);
}

function renderResults(data) {
  const rs = document.getElementById('results-section');

  const typeOrder = ['risky','balanced','safe'];
  const sorted = [...data.flights].sort((a,b) => typeOrder.indexOf(a.type) - typeOrder.indexOf(b.type));

  let cardsHTML = sorted.map(f => `
    <div class="flight-card ${f.type}">
      <div class="fc-header">
        <span class="fc-tag">${f.typeLabel}</span>
        <div class="fc-flight-number">${f.flightNumber}</div>
        <div class="fc-route">${f.aircraft}</div>
      </div>
      <div class="fc-times">
        <div class="fc-time-block">
          <div class="fc-time">${f.depTime}</div>
          <div class="fc-airport">${f.depAirport}</div>
        </div>
        <div class="fc-duration">
          <div>${f.duration}</div>
          <div class="fc-dur-line"></div>
          <div>nonstop</div>
        </div>
        <div class="fc-time-block" style="text-align:right">
          <div class="fc-time">${f.arrTime}</div>
          <div class="fc-airport">${f.arrAirport}</div>
        </div>
      </div>
      <div class="fc-factors">
        <div class="fc-factor">
          <span class="fc-factor-label">🛂 TSA wait</span>
          <span class="fc-factor-val ${f.tsaColor}">${f.tsaWait}</span>
        </div>
        <div class="fc-factor">
          <span class="fc-factor-label">🚆 Transit downtown</span>
          <span class="fc-factor-val val-blue" style="font-size:10px">${f.transitOption}</span>
        </div>
        <div class="fc-factor">
          <span class="fc-factor-label">✅ On-time</span>
          <span class="fc-factor-val ${f.onTimeColor}">${f.onTimePercent}</span>
        </div>
        <div class="fc-factor">
          <span class="fc-factor-label">⏱ Buffer time</span>
          <span class="fc-factor-val">${f.bufferTime}</span>
        </div>
        ${f.riskNote ? `<div style="font-size:11px;color:#7a5010;background:var(--gold-light);padding:7px 10px;border-radius:7px;margin-top:4px;line-height:1.5;">${f.riskNote}</div>` : ''}
      </div>
      <div class="fc-score">
        <span class="fc-score-label">AI ${f.confidence}%</span>
        <div class="fc-score-bar"><div class="fc-score-fill" style="width:${f.confidence}%"></div></div>
        <span style="font-size:13px;font-weight:600;color:var(--text-primary);">${f.price}</span>
      </div>
      <a class="book-btn" href="https://www.united.com" target="_blank">Book this flight →</a>
    </div>`).join('');

  rs.innerHTML = `
    <div class="results-header">
      <h3>Recommended flights</h3>
      <span>${data.routeSummary} · ${(data.travelerName||'TRAVELER').toUpperCase()}</span>
    </div>
    <div class="results-explainer">${data.explainer}</div>
    <div class="flight-cards">${cardsHTML}</div>
    <div class="ai-reasoning">
      <div class="ai-reasoning-header">
        <div class="ai-dot"></div>
        <span>AI REASONING</span>
      </div>
      <p>${data.aiReasoning}</p>
    </div>`;

  rs.style.display = 'block';
  rs.scrollIntoView({ behavior: 'smooth', block: 'start' });
}
</script>
</body>
</html>
