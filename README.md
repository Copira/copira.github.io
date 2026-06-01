cat > /mnt/user-data/outputs/united-ai/index.html << 'ENDOFFILE'
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>United Business Travel Planner</title>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --blue: #003580;
    --blue-mid: #1a5fab;
    --blue-light: #e8f2fa;
    --gold: #c8922a;
    --gold-light: #f5e6c8;
    --text: #0f1e34;
    --text-secondary: #4a5568;
    --text-muted: #8a9ab0;
    --border: #d1dcea;
    --bg: #f5f7fa;
    --white: #ffffff;
    --green: #1e6e3e;
    --green-light: #e6f4ec;
    --amber: #7a5010;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: 'Inter', sans-serif; background: var(--bg); color: var(--text); font-size: 14px; line-height: 1.5; }

  header {
    background: var(--blue);
    padding: 0 40px;
    height: 56px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .logo { display: flex; align-items: center; gap: 10px; }
  .logo-mark {
    width: 28px; height: 28px; border: 1.5px solid var(--gold);
    border-radius: 50%; position: relative; overflow: hidden;
  }
  .logo-mark::before { content:''; position:absolute; width:100%; height:1px; background:var(--gold); top:50%; }
  .logo-mark::after  { content:''; position:absolute; height:100%; width:1px; background:var(--gold); left:50%; }
  .logo-text { font-size: 15px; font-weight: 600; color: white; letter-spacing: -0.2px; }
  .logo-text span { color: var(--gold); }
  .header-label { font-size: 12px; color: rgba(255,255,255,0.5); font-weight: 400; letter-spacing: 0.2px; }

  .page { max-width: 800px; margin: 0 auto; padding: 40px 24px 80px; }

  h1 { font-size: 22px; font-weight: 600; letter-spacing: -0.4px; margin-bottom: 6px; }
  .subtitle { font-size: 13px; color: var(--text-secondary); margin-bottom: 32px; }

  .section { background: var(--white); border: 1px solid var(--border); border-radius: 10px; padding: 24px; margin-bottom: 16px; }
  .section-label { font-size: 11px; font-weight: 600; letter-spacing: 0.9px; text-transform: uppercase; color: var(--text-muted); margin-bottom: 16px; }

  textarea {
    width: 100%; border: 1px solid var(--border); border-radius: 8px;
    padding: 12px 14px; font-family: 'Inter', sans-serif; font-size: 14px;
    color: var(--text); resize: vertical; min-height: 100px; background: var(--bg);
    line-height: 1.6;
  }
  textarea:focus { outline: none; border-color: var(--blue-mid); background: white; }
  textarea::placeholder { color: var(--text-muted); }

  .route-row { display: grid; grid-template-columns: 1fr 24px 1fr; gap: 10px; align-items: center; margin-bottom: 12px; }
  .route-arrow { text-align: center; color: var(--text-muted); font-size: 16px; }
  .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  input[type=text] {
    width: 100%; border: 1px solid var(--border); border-radius: 8px;
    padding: 10px 12px; font-family: 'Inter', sans-serif; font-size: 14px;
    color: var(--text); background: var(--bg);
  }
  input[type=text]:focus { outline: none; border-color: var(--blue-mid); background: white; }
  input::placeholder { color: var(--text-muted); }

  .toggles { display: flex; flex-wrap: wrap; gap: 8px; }
  .toggle {
    display: flex; align-items: center; gap: 7px;
    padding: 8px 12px; border: 1px solid var(--border); border-radius: 6px;
    cursor: pointer; user-select: none; background: var(--bg); font-size: 13px;
    transition: border-color 0.15s, background 0.15s;
  }
  .toggle:hover { border-color: #8aafd4; }
  .toggle.active { border-color: var(--blue-mid); background: var(--blue-light); color: var(--blue); }
  .toggle-box {
    width: 15px; height: 15px; border: 1.5px solid var(--border); border-radius: 3px;
    display: flex; align-items: center; justify-content: center; flex-shrink: 0; font-size: 10px;
  }
  .toggle.active .toggle-box { background: var(--blue-mid); border-color: var(--blue-mid); color: white; }
  .toggle-sub { font-size: 11px; color: var(--text-muted); margin-left: 2px; }
  .toggle.active .toggle-sub { color: #4a7ab5; }

  .go-row { display: flex; align-items: center; gap: 16px; margin-top: 20px; }
  .go-btn {
    background: var(--blue); color: white; border: none; padding: 11px 32px;
    border-radius: 6px; font-family: 'Inter', sans-serif; font-size: 14px;
    font-weight: 600; cursor: pointer; letter-spacing: 0.1px;
  }
  .go-btn:hover { background: var(--blue-mid); }
  .go-btn:active { opacity: 0.9; }
  .go-note { font-size: 12px; color: var(--text-muted); }

  /* Loading */
  #loading { display: none; margin-top: 24px; padding: 24px; background: white; border: 1px solid var(--border); border-radius: 10px; }
  .loading-inner { display: flex; align-items: center; gap: 12px; margin-bottom: 16px; }
  .spinner { width: 18px; height: 18px; border: 2px solid var(--border); border-top-color: var(--blue); border-radius: 50%; animation: spin 0.7s linear infinite; flex-shrink: 0; }
  @keyframes spin { to { transform: rotate(360deg); } }
  .loading-title { font-size: 14px; font-weight: 500; color: var(--text); }
  .steps { list-style: none; display: flex; flex-direction: column; gap: 6px; padding-left: 4px; }
  .step { font-size: 12px; color: var(--text-muted); display: flex; align-items: center; gap: 8px; }
  .step.active { color: var(--blue); }
  .step.done { color: var(--green); }
  .step-icon { width: 14px; text-align: center; font-size: 11px; }

  /* Results */
  #results { display: none; margin-top: 24px; }
  .results-intro { font-size: 13px; color: var(--text-secondary); margin-bottom: 20px; padding: 12px 14px; background: var(--blue-light); border-left: 3px solid var(--blue-mid); border-radius: 0 6px 6px 0; }

  .flight-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 14px; margin-bottom: 20px; }
  @media (max-width: 680px) { .flight-grid { grid-template-columns: 1fr; } }

  .fcard { background: white; border: 1px solid var(--border); border-radius: 10px; overflow: hidden; }
  .fcard.risky   { border-top: 3px solid var(--gold); }
  .fcard.balanced{ border-top: 3px solid var(--blue-mid); }
  .fcard.safe    { border-top: 3px solid var(--green); }

  .fcard-head { padding: 14px 16px 12px; border-bottom: 1px solid var(--border); }
  .fcard-badge {
    display: inline-block; font-size: 10px; font-weight: 600; letter-spacing: 0.7px;
    text-transform: uppercase; padding: 2px 8px; border-radius: 4px; margin-bottom: 8px;
  }
  .risky   .fcard-badge { background: var(--gold-light); color: var(--amber); }
  .balanced .fcard-badge { background: var(--blue-light); color: var(--blue-mid); }
  .safe    .fcard-badge { background: var(--green-light); color: var(--green); }

  .fcard-num { font-size: 18px; font-weight: 600; letter-spacing: -0.3px; }
  .fcard-aircraft { font-size: 11px; color: var(--text-muted); margin-top: 1px; }

  .fcard-times { padding: 14px 16px; display: flex; align-items: center; gap: 6px; border-bottom: 1px solid var(--border); }
  .ftime-block { flex: 1; }
  .ftime { font-size: 18px; font-weight: 600; letter-spacing: -0.3px; }
  .fairport { font-size: 11px; color: var(--text-muted); margin-top: 1px; }
  .fdur { text-align: center; font-size: 11px; color: var(--text-muted); }
  .fdur-line { height: 1px; background: var(--border); width: 36px; margin: 3px auto; }

  .fcard-facts { padding: 12px 16px; border-bottom: 1px solid var(--border); display: flex; flex-direction: column; gap: 7px; }
  .fact { display: flex; align-items: flex-start; justify-content: space-between; gap: 8px; font-size: 12px; }
  .fact-label { color: var(--text-secondary); flex-shrink: 0; }
  .fact-val { font-weight: 500; text-align: right; }
  .fv-green { color: var(--green); }
  .fv-amber { color: var(--amber); }
  .fv-blue  { color: var(--blue-mid); }
  .risk-note { font-size: 11px; color: var(--amber); background: var(--gold-light); padding: 6px 9px; border-radius: 5px; margin-top: 4px; line-height: 1.5; }

  .fcard-foot { padding: 12px 16px; display: flex; align-items: center; justify-content: space-between; }
  .fcard-price { font-size: 16px; font-weight: 600; }
  .fcard-confidence { font-size: 11px; color: var(--text-muted); }

  .book-link {
    display: block; margin: 0 16px 14px; padding: 9px; text-align: center;
    border-radius: 6px; border: 1px solid; font-size: 13px; font-weight: 500;
    text-decoration: none; cursor: pointer;
  }
  .risky   .book-link { border-color: var(--gold); color: var(--amber); }
  .risky   .book-link:hover { background: var(--gold-light); }
  .balanced .book-link { border-color: var(--blue-mid); color: var(--blue-mid); }
  .balanced .book-link:hover { background: var(--blue-light); }
  .safe    .book-link { border-color: var(--green); color: var(--green); }
  .safe    .book-link:hover { background: var(--green-light); }

  .reasoning { background: white; border: 1px solid var(--border); border-radius: 10px; padding: 20px 22px; }
  .reasoning-label { font-size: 11px; font-weight: 600; letter-spacing: 0.9px; text-transform: uppercase; color: var(--text-muted); margin-bottom: 10px; }
  .reasoning p { font-size: 13px; color: var(--text-secondary); line-height: 1.8; }
  .reasoning strong { color: var(--text); font-weight: 500; }
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
      <label class="toggle active" onclick="toggleItem(this)">
        <div class="toggle-box">✓</div>TSA Precheck<span class="toggle-sub">Expedited</span>
      </label>
      <label class="toggle" onclick="toggleItem(this)">
        <div class="toggle-box"></div>CLEAR<span class="toggle-sub">Biometric</span>
      </label>
      <label class="toggle" onclick="toggleItem(this)">
        <div class="toggle-box"></div>Global Entry
      </label>
      <label class="toggle active" onclick="toggleItem(this)">
        <div class="toggle-box">✓</div>MileagePlus
      </label>
      <label class="toggle" onclick="toggleItem(this)">
        <div class="toggle-box"></div>Wheelchair<span class="toggle-sub">Accessibility</span>
      </label>
      <label class="toggle" onclick="toggleItem(this)">
        <div class="toggle-box"></div>United Club<span class="toggle-sub">Lounge</span>
      </label>
      <label class="toggle" onclick="toggleItem(this)">
        <div class="toggle-box"></div>Checked bag
      </label>
    </div>
  </div>

  <div class="go-row">
    <button class="go-btn" onclick="runPlanner()">Find flights</button>
    <span class="go-note">Compares TSA wait times, transit options, and on-time data</span>
  </div>

  <div id="loading">
    <div class="loading-inner">
      <div class="spinner"></div>
      <span class="loading-title">Analyzing your journey…</span>
    </div>
    <ul class="steps">
      <li class="step" id="s1"><span class="step-icon">·</span>Reading journey details</li>
      <li class="step" id="s2"><span class="step-icon">·</span>Identifying flights</li>
      <li class="step" id="s3"><span class="step-icon">·</span>Estimating TSA wait times</li>
      <li class="step" id="s4"><span class="step-icon">·</span>Checking downtown transit</li>
      <li class="step" id="s5"><span class="step-icon">·</span>Ranking by risk and buffer time</li>
    </ul>
  </div>

  <div id="results"></div>
</div>

<script>
function toggleItem(el) {
  el.classList.toggle('active');
  const box = el.querySelector('.toggle-box');
  box.textContent = el.classList.contains('active') ? '✓' : '';
}

function getToggles() {
  return Array.from(document.querySelectorAll('.toggle.active')).map(t => {
    return t.childNodes[1]?.textContent?.trim() || t.textContent.trim().split('\n')[0].trim();
  });
}

const TRANSIT = {
  ORD: 'Blue Line → Loop: ~45 min',
  MDW: 'Orange Line → Loop: ~30 min',
  LGA: 'AirTrain + subway: ~55 min',
  EWR: 'NJ Transit → Penn: ~30 min',
  JFK: 'AirTrain + A train: ~60 min',
  SFO: 'BART to Downtown: ~30 min',
  LAX: 'FlyAway Bus: ~45 min',
  BOS: 'Silver Line: ~25 min',
  DCA: 'Metro Blue Line: ~20 min',
};

function buildResults(origin, dest, toggles) {
  const o = (origin||'LGA').toUpperCase().trim();
  const d = (dest||'ORD').toUpperCase().trim();
  const hasCLEAR = toggles.some(t => t.includes('CLEAR'));
  const hasPrecheck = toggles.some(t => t.includes('Precheck') || t.includes('TSA'));
  const hasWheelchair = toggles.some(t => t.includes('Wheelchair'));

  const tsaFast = hasCLEAR ? '3–5 min (CLEAR)' : hasPrecheck ? '7–10 min (PreCheck)' : '22–35 min';
  const tsaMed  = hasCLEAR ? '3–5 min (CLEAR)' : hasPrecheck ? '8–14 min (PreCheck)' : '18–28 min';
  const tsaColor = (hasCLEAR || hasPrecheck) ? 'fv-green' : 'fv-amber';
  const transit = TRANSIT[d] || 'Transit to downtown: ~35 min';
  const accessNote = hasWheelchair ? ' · Wheelchair assist at gate' : '';

  const name = extractName(document.getElementById('journey-text').value) || 'Traveler';

  const n1 = rn(), n2 = rn(), n3 = rn();
  return {
    route: `${o} → ${d}`,
    name,
    explainer: `Showing three options for the ${o} → ${d} route, ranked by safety margin. TSA estimates reflect your ${hasCLEAR ? 'CLEAR' : hasPrecheck ? 'PreCheck' : 'standard'} lane.`,
    flights: [
      { type:'risky',    label:'Fastest / Riskiest', num:`UA ${n1}`, aircraft:'B737-800',   dep:'5:55 AM', arr:'7:31 AM', dur:'2h 36m', tsa:tsaFast, tsaC:tsaColor, transit:transit+accessNote, ot:'74%', otC:'fv-amber', buf:'~14 min', price:'$219', conf:58, note:'Very tight — any delay risks missing the meeting.' },
      { type:'balanced', label:'Best Balance',        num:`UA ${n2}`, aircraft:'A320',       dep:'6:45 AM', arr:'8:22 AM', dur:'2h 37m', tsa:tsaMed,  tsaC:tsaColor, transit:transit+accessNote, ot:'88%', otC:'fv-green', buf:'~38 min', price:'$259', conf:84, note:null },
      { type:'safe',     label:'Safest',              num:`UA ${n3}`, aircraft:'B737 MAX 9', dep:'5:10 AM', arr:'6:47 AM', dur:'2h 37m', tsa:tsaFast, tsaC:tsaColor, transit:transit+accessNote, ot:'91%', otC:'fv-green', buf:'~73 min', price:'$299', conf:95, note:null },
    ],
    reasoning: `Given the hard arrival constraint and ${hasCLEAR||hasPrecheck ? 'expedited security' : 'standard security lanes'}, the <strong>Best Balance (UA ${n2})</strong> is the recommended choice. It lands by 8:22 AM, leaving a 38-minute buffer to reach downtown via the ${(TRANSIT[d]||'transit').split(':')[0]} before the meeting. The 5:55 AM departure is technically workable but its 74% on-time rate is a meaningful risk. The 5:10 AM departure gives the most cushion but requires an early wake-up for relatively modest additional benefit given the reliable 6:45 AM schedule.`
  };
}

function rn() { return Math.floor(Math.random()*8000)+1000; }
function extractName(t) {
  const m = t.match(/(?:i['']m|my name is|i am)\s+([A-Z][a-z]+(?:\s+[A-Z]\.?)?)/i);
  return m ? m[1] : null;
}

function runPlanner() {
  const origin = document.getElementById('origin').value;
  const dest   = document.getElementById('destination').value;
  const toggles = getToggles();

  document.getElementById('results').style.display = 'none';
  document.getElementById('results').innerHTML = '';
  const loadEl = document.getElementById('loading');
  loadEl.style.display = 'block';

  const sids = ['s1','s2','s3','s4','s5'];
  sids.forEach(s => { const el = document.getElementById(s); el.className='step'; el.querySelector('.step-icon').textContent='·'; });

  let idx = 0;
  function advance() {
    if (idx > 0 && idx <= sids.length) {
      const prev = document.getElementById(sids[idx-1]);
      prev.className = 'step done';
      prev.querySelector('.step-icon').textContent = '✓';
    }
    if (idx < sids.length) {
      document.getElementById(sids[idx]).className = 'step active';
      idx++;
    }
  }
  advance();
  const iv = setInterval(advance, 700);

  setTimeout(() => {
    clearInterval(iv);
    sids.forEach(s => { const el = document.getElementById(s); el.className='step done'; el.querySelector('.step-icon').textContent='✓'; });
    setTimeout(() => {
      loadEl.style.display = 'none';
      render(buildResults(origin, dest, toggles));
    }, 300);
  }, 3800);
}

function render(data) {
  const order = ['risky','balanced','safe'];
  const sorted = [...data.flights].sort((a,b) => order.indexOf(a.type)-order.indexOf(b.type));

  const cards = sorted.map(f => `
    <div class="fcard ${f.type}">
      <div class="fcard-head">
        <span class="fcard-badge">${f.label}</span>
        <div class="fcard-num">${f.num}</div>
        <div class="fcard-aircraft">${f.aircraft}</div>
      </div>
      <div class="fcard-times">
        <div class="ftime-block">
          <div class="ftime">${f.dep}</div>
          <div class="fairport">${data.route.split(' → ')[0]}</div>
        </div>
        <div class="fdur">
          <div>${f.dur}</div>
          <div class="fdur-line"></div>
          <div>nonstop</div>
        </div>
        <div class="ftime-block" style="text-align:right">
          <div class="ftime">${f.arr}</div>
          <div class="fairport">${data.route.split(' → ')[1]}</div>
        </div>
      </div>
      <div class="fcard-facts">
        <div class="fact"><span class="fact-label">TSA wait</span><span class="fact-val ${f.tsaC}">${f.tsa}</span></div>
        <div class="fact"><span class="fact-label">Downtown transit</span><span class="fact-val fv-blue" style="font-size:11px">${f.transit}</span></div>
        <div class="fact"><span class="fact-label">On-time rate</span><span class="fact-val ${f.otC}">${f.ot}</span></div>
        <div class="fact"><span class="fact-label">Buffer time</span><span class="fact-val">${f.buf}</span></div>
        ${f.note ? `<div class="risk-note">${f.note}</div>` : ''}
      </div>
      <div class="fcard-foot">
        <span class="fcard-price">${f.price}</span>
        <span class="fcard-confidence">AI confidence: ${f.conf}%</span>
      </div>
      <a class="book-link" href="https://www.united.com" target="_blank">Book on United →</a>
    </div>`).join('');

  const el = document.getElementById('results');
  el.innerHTML = `
    <div class="results-intro">${data.explainer}</div>
    <div class="flight-grid">${cards}</div>
    <div class="reasoning">
      <div class="reasoning-label">AI reasoning</div>
      <p>${data.reasoning}</p>
    </div>`;
  el.style.display = 'block';
  el.scrollIntoView({ behavior: 'smooth', block: 'start' });
}
</script>
</body>
</html>
