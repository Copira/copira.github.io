<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>United Business Travel Planner</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --blue: #003580; --blue-mid: #1a5fab; --blue-light: #e8f2fa;
    --gold: #c8922a; --gold-light: #f5e6c8;
    --text: #0f1e34; --text-secondary: #4a5568; --text-muted: #8a9ab0;
    --border: #d1dcea; --bg: #f5f7fa; --white: #ffffff;
    --green: #1e6e3e; --green-light: #e6f4ec; --amber: #7a5010;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'Inter', sans-serif; background: var(--bg); color: var(--text); font-size: 14px; line-height: 1.5; }

  header { background: var(--blue); padding: 0 40px; height: 56px; display: flex; align-items: center; justify-content: space-between; }
  .logo { display: flex; align-items: center; gap: 10px; }
  .logo-mark { width: 28px; height: 28px; border: 1.5px solid var(--gold); border-radius: 50%; position: relative; overflow: hidden; }
  .logo-mark::before { content:''; position:absolute; width:100%; height:1px; background:var(--gold); top:50%; }
  .logo-mark::after  { content:''; position:absolute; height:100%; width:1px; background:var(--gold); left:50%; }
  .logo-text { font-size: 15px; font-weight: 600; color: white; letter-spacing: -0.2px; }
  .logo-text span { color: var(--gold); }
  .header-label { font-size: 12px; color: rgba(255,255,255,0.5); }

  .page { max-width: 800px; margin: 0 auto; padding: 40px 24px 80px; }
  h1 { font-size: 22px; font-weight: 600; letter-spacing: -0.4px; margin-bottom: 6px; }
  .subtitle { font-size: 13px; color: var(--text-secondary); margin-bottom: 32px; }

  .section { background: var(--white); border: 1px solid var(--border); border-radius: 10px; padding: 24px; margin-bottom: 16px; }
  .section-label { font-size: 11px; font-weight: 600; letter-spacing: 0.9px; text-transform: uppercase; color: var(--text-muted); margin-bottom: 16px; }

  textarea { width: 100%; border: 1px solid var(--border); border-radius: 8px; padding: 12px 14px; font-family: 'Inter', sans-serif; font-size: 14px; color: var(--text); resize: vertical; min-height: 100px; background: var(--bg); line-height: 1.6; }
  textarea:focus { outline: none; border-color: var(--blue-mid); background: white; }
  textarea::placeholder { color: var(--text-muted); }

  .route-row { display: grid; grid-template-columns: 1fr 24px 1fr; gap: 10px; align-items: center; margin-bottom: 12px; }
  .route-arrow { text-align: center; color: var(--text-muted); font-size: 16px; }
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  input[type=text] { width: 100%; border: 1px solid var(--border); border-radius: 8px; padding: 10px 12px; font-family: 'Inter', sans-serif; font-size: 14px; color: var(--text); background: var(--bg); }
  input[type=text]:focus { outline: none; border-color: var(--blue-mid); background: white; }
  input::placeholder { color: var(--text-muted); }

  .toggles { display: flex; flex-wrap: wrap; gap: 8px; }
  .toggle { display: flex; align-items: center; gap: 7px; padding: 8px 12px; border: 1px solid var(--border); border-radius: 6px; cursor: pointer; user-select: none; background: var(--bg); font-size: 13px; transition: border-color 0.15s, background 0.15s; }
  .toggle:hover { border-color: #8aafd4; }
  .toggle.active { border-color: var(--blue-mid); background: var(--blue-light); color: var(--blue); }
  .toggle-box { width: 15px; height: 15px; border: 1.5px solid var(--border); border-radius: 3px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; font-size: 10px; }
  .toggle.active .toggle-box { background: var(--blue-mid); border-color: var(--blue-mid); color: white; }
  .toggle-sub { font-size: 11px; color: var(--text-muted); margin-left: 2px; }
  .toggle.active .toggle-sub { color: #4a7ab5; }

  .go-row { display: flex; align-items: center; gap: 16px; margin-top: 20px; }
  .go-btn { background: var(--blue); color: white; border: none; padding: 11px 32px; border-radius: 6px; font-family: 'Inter', sans-serif; font-size: 14px; font-weight: 600; cursor: pointer; }
  .go-btn:hover { background: var(--blue-mid); }
  .go-note { font-size: 12px; color: var(--text-muted); }
</style>
</head>
<body>
<header>
  <div class="logo">
    <div class="logo-mark"></div>
    <span class="logo-text">United <span>AI</span></span>
  </div>
  <span class="header-label">Business Travel Planner · ORD / LGA / EWR</span>
</header>

<div class="page">
  <h1>Business travel planner</h1>
  <p class="subtitle">Describe your trip and we'll compare flights by TSA wait time, downtown transit, and on-time reliability — then suggest the three best options.</p>

  <div class="section">
    <div class="section-label">Journey description</div>
    <textarea id="journey-text" placeholder="e.g. I'm Joe G, flying LGA to ORD tomorrow morning for a 10am meeting in the Loop. Need to arrive by 9am.">I'm Joe G. I'm flying from LaGuardia to Chicago O'Hare tomorrow morning for a 9:30am client meeting in the Loop. I need to be downtown no later than 9am.</textarea>
  </div>

  <div class="section">
    <div class="section-label">Route & timing</div>
    <div class="route-row">
      <input type="text" id="origin" placeholder="Origin airport (e.g. LGA)" value="LGA" />
      <div class="route-arrow">→</div>
      <input type="text" id="destination" placeholder="Destination (e.g. ORD)" value="ORD" />
    </div>
    <div class="two-col">
      <input type="text" id="travel-date" placeholder="Travel date" value="Tomorrow" />
      <input type="text" id="must-arrive" placeholder="Must arrive by" value="9:00 AM" />
    </div>
  </div>

  <div class="section">
    <div class="section-label">Your services & preferences</div>
    <div class="toggles">
      <label class="toggle active" onclick="toggleItem(this)"><div class="toggle-box">✓</div>TSA Precheck<span class="toggle-sub">Expedited</span></label>
      <label class="toggle" onclick="toggleItem(this)"><div class="toggle-box"></div>CLEAR<span class="toggle-sub">Biometric</span></label>
      <label class="toggle" onclick="toggleItem(this)"><div class="toggle-box"></div>Global Entry</label>
      <label class="toggle active" onclick="toggleItem(this)"><div class="toggle-box">✓</div>MileagePlus</label>
      <label class="toggle" onclick="toggleItem(this)"><div class="toggle-box"></div>Wheelchair<span class="toggle-sub">Accessibility</span></label>
      <label class="toggle" onclick="toggleItem(this)"><div class="toggle-box"></div>United Club<span class="toggle-sub">Lounge</span></label>
      <label class="toggle" onclick="toggleItem(this)"><div class="toggle-box"></div>Checked bag</label>
    </div>
  </div>

  <div class="go-row">
    <button class="go-btn" onclick="goToResults()">Find flights</button>
    <span class="go-note">Compares TSA wait times, transit options, and on-time data</span>
  </div>
</div>

<script>
function toggleItem(el) {
  el.classList.toggle('active');
  el.querySelector('.toggle-box').textContent = el.classList.contains('active') ? '✓' : '';
}

function goToResults() {
  const params = new URLSearchParams({
    journey:  document.getElementById('journey-text').value,
    origin:   document.getElementById('origin').value,
    dest:     document.getElementById('destination').value,
    date:     document.getElementById('travel-date').value,
    arrive:   document.getElementById('must-arrive').value,
    toggles:  Array.from(document.querySelectorAll('.toggle.active')).map(t =>
                t.childNodes[1]?.textContent?.trim() || '').filter(Boolean).join(',')
  });
  window.location.href = 'results.html?' + params.toString();
}
</script>
</body>
</html>
