<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>ParkPal — Log in</title>
  <meta name="description" content="Log in to ParkPal to reserve bays and view live availability.">
  <meta name="theme-color" content="#c1121f">
  <style>
    :root{
      --accent:#c1121f; --accent-600:#a50e19; --accent-light:#ff4d4d;
      --bg:#fff8f8; --bg-2:#ffeaea; --text:#0f1724; --muted:#6b7280;
      --card:#ffffff; --border:rgba(15,23,36,0.08); --shadow:0 6px 20px rgba(193,18,31,0.08);
      --input:#ffffff; --error:#b91c1c; --ok:#065f46;
    }
    @media (prefers-color-scheme: dark){
      :root{
        --bg:#0d0f13; --bg-2:#12151b; --text:#eef2ff; --muted:#a6adbb;
        --card:#121720; --input:#0f141c; --border:rgba(255,255,255,0.12);
        --shadow:0 10px 30px rgba(0,0,0,0.4);
      }
    }
    *{box-sizing:border-box}
    body{
      margin:0; font-family:Inter,system-ui,-apple-system,'Segoe UI',Roboto,Arial,sans-serif;
      color:var(--text);
      background:linear-gradient(180deg,var(--bg),var(--bg-2)) fixed;
      min-height:100svh; display:grid; place-items:center;
    }
    .wrap{width:min(100%, 900px); padding:24px}
    .topbar{background:var(--accent); color:#fff; text-align:center; padding:6px 0; font-weight:600; border-radius:10px; margin-bottom:18px}
    .card{background:var(--card); border:1px solid var(--border); border-radius:16px; box-shadow:var(--shadow)}
    .grid{display:grid; grid-template-columns:1fr 1fr; gap:28px}
    @media (max-width:900px){.grid{grid-template-columns:1fr}}
    .left{padding:26px}
    .right{padding:26px; border-left:1px solid var(--border); display:grid; place-items:center}
    @media (max-width:900px){.right{display:none}}
    .logo{display:inline-flex; gap:8px; align-items:center; font-weight:800; color:#fff;
      background:linear-gradient(135deg,var(--accent),var(--accent-light));
      padding:8px 12px; border-radius:12px; box-shadow:0 4px 10px rgba(193,18,31,0.3);}
    .logo svg{width:18px;height:18px}
    h1{margin:.4rem 0 0; font-size:26px}
    p.lead{color:var(--muted); margin:.3rem 0 1rem}
    form{display:grid; gap:14px; margin-top:8px}
    label{font-weight:600}
    .field{display:grid; gap:6px}
    .control{position:relative}
    input[type="email"],input[type="password"],input[type="text"]{
      width:100%; padding:12px 14px; border-radius:10px; border:1px solid var(--border);
      background:var(--input); color:inherit; font-size:16px;
    }
    .toggle{
      position:absolute; right:8px; top:50%; transform:translateY(-50%);
      background:transparent; border:0; padding:6px 8px; cursor:pointer; color:var(--muted);
    }
    .btn{background:var(--accent); color:#fff; border:0; padding:12px 16px; border-radius:10px; font-weight:700; cursor:pointer; width:100%}
    .btn:hover{background:var(--accent-600)}
    .btn.ghost{background:transparent; color:var(--accent); border:1px solid rgba(193,18,31,.35); width:auto}
    .row{display:flex; justify-content:space-between; align-items:center; gap:10px; flex-wrap:wrap}
    .checkbox{display:flex; align-items:center; gap:8px; color:var(--muted)}
    .links{display:flex; justify-content:space-between; gap:10px; flex-wrap:wrap; margin-top:2px}
    .links a{color:var(--accent-600); text-decoration:none}
    .links a:hover{text-decoration:underline}
    .hint{font-size:12px; color:var(--muted)}
    .error{color:var(--error); font-size:13px}
    .sr-only{position:absolute; width:1px; height:1px; padding:0; margin:-1px; overflow:hidden; clip:rect(0,0,0,0); white-space:nowrap; border:0}
    /* Inline signup section (no separate page) */
    details.signup{margin-top:10px}
    details.signup summary{cursor:pointer; color:var(--accent-600); font-weight:700}
    .meter{height:8px; border-radius:6px; background:#e5e7eb; overflow:hidden; border:1px solid var(--border); margin-top:4px}
    .meter>span{display:block; height:100%; width:0%}
    .meter[data-level="1"]>span{width:33%}
    .meter[data-level="2"]>span{width:66%}
    .meter[data-level="3"]>span{width:100%}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="topbar">Zayed University — Abu Dhabi campus</div>

    <div class="card grid" role="main" aria-labelledby="login-title">
      <!-- LEFT: Login -->
      <section class="left">
        <div class="logo" aria-label="ParkPal logo">
          <span>P</span>
          <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M5 11l1-3a3 3 0 012.83-2h6.34A3 3 0 0118 8l1 3h1a1 1 0 010 2h-1v3a1 1 0 01-1 1h-1a2 2 0 01-4 0H10a2 2 0 01-4 0H5a1 1 0 01-1-1v-3H3a1 1 0 110-2h2zm3.17-4a1 1 0 00-.95.68L6.6 11h10.8l-.62-3.32a1 1 0 00-.98-.68H8.17zM7 16a1 1 0 102 0 1 1 0 00-2 0zm8 0a1 1 0 102 0 1 1 0 00-2 0z"/></svg>
          <span>PARK</span><span>PAL</span>
        </div>
        <h1 id="login-title">Welcome to ParkPal</h1>
        <p class="lead">Log in with your university email to continue.</p>

        <form id="loginForm" novalidate>
          <div class="field">
            <label for="email">Email address</label>
            <div class="control">
              <input id="email" name="email" type="email" inputmode="email" autocomplete="email" required placeholder="you@zayedu.ac.ae" aria-describedby="email-error">
            </div>
            <div id="email-error" class="error" role="alert" aria-live="polite"></div>
          </div>

          <div class="field">
            <label for="password">Password</label>
            <div class="control">
              <input id="password" name="password" type="password" minlength="8" autocomplete="current-password" required placeholder="••••••••" aria-describedby="password-error">
              <button type="button" class="toggle" id="togglePwd" aria-pressed="false" aria-label="Show password">Show</button>
            </div>
            <div id="password-error" class="error" role="alert" aria-live="polite"></div>
          </div>

          <div class="row">
            <label class="checkbox"><input type="checkbox" id="remember"> <span>Remember me</span></label>
            <a href="#" class="hint" id="forgotLink">Forgot password?</a>
          </div>

          <button class="btn" type="submit">Log in</button>

          <!-- Inline Sign-up (no separate page) -->
          <details class="signup">
            <summary>New here? Create an account</summary>
            <div style="margin-top:10px; display:grid; gap:12px">
              <div class="field">
                <label for="s-name">Full name</label>
                <input id="s-name" type="text" autocomplete="name" placeholder="Your name">
              </div>
              <div class="field">
                <label for="s-email">University email</label>
                <input id="s-email" type="email" autocomplete="email" placeholder="you@zayedu.ac.ae">
              </div>
              <div class="field">
                <label for="s-pass">Password</label>
                <div class="control">
                  <input id="s-pass" type="password" autocomplete="new-password" minlength="8" placeholder="Create a password">
                  <button type="button" class="toggle" id="toggleNew" aria-pressed="false" aria-label="Show password">Show</button>
                </div>
                <div class="meter" id="strength"><span></span></div>
              </div>
              <div class="field">
                <label for="s-confirm">Confirm password</label>
                <div class="control">
                  <input id="s-confirm" type="password" autocomplete="new-password" minlength="8" placeholder="Repeat password">
                  <button type="button" class="toggle" id="toggleConfirm" aria-pressed="false" aria-label="Show password">Show</button>
                </div>
              </div>
              <label class="checkbox"><input type="checkbox" id="s-terms"> <span>I agree to the Terms & Privacy Policy.</span></label>
              <button class="btn" type="button" id="createBtn">Create account</button>
              <div class="hint" id="createMsg" aria-live="polite"></div>
            </div>
          </details>

          <p id="form-status" class="sr-only" role="status" aria-live="polite"></p>
        </form>
      </section>

      <!-- RIGHT: Info -->
      <aside class="right" aria-hidden="true">
        <div>
          <h2>Beat the parking rush 🚗</h2>
          <p class="hint">Check real-time bays, reserve a spot, and get guided directions.</p>
          <a class="btn ghost" href="index.html">← Back to home</a>
        </div>
      </aside>
    </div>
  </div>

  <script>
    // Shorthands
    const $ = s => document.querySelector(s);
    const emailRe = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

    // Login
    const loginForm = $('#loginForm');
    const email = $('#email');
    const password = $('#password');
    const emailErr = $('#email-error');
    const pwdErr = $('#password-error');
    const statusEl = $('#form-status');

    $('#togglePwd').addEventListener('click', () => {
      const isText = password.type === 'text';
      password.type = isText ? 'password' : 'text';
      event.target.textContent = isText ? 'Show' : 'Hide';
      event.target.setAttribute('aria-pressed', String(!isText));
    });

    loginForm.addEventListener('submit', (e) => {
      e.preventDefault();
      emailErr.textContent = ''; pwdErr.textContent = ''; statusEl.textContent = '';

      let ok = true;
      if (!email.value.trim()){ emailErr.textContent = 'Email is required.'; ok = false; }
      else if (!emailRe.test(email.value.trim())){ emailErr.textContent = 'Enter a valid email.'; ok = false; }

      if (!password.value){ pwdErr.textContent = 'Password is required.'; ok = false; }
      else if (password.value.length < 8){ pwdErr.textContent = 'Minimum 8 characters.'; ok = false; }

      if (!ok){ statusEl.textContent = 'Please fix the highlighted fields.'; return; }

      statusEl.textContent = 'Signing you in…';
      setTimeout(()=>{ window.location.href = 'index.html#app'; }, 500);
    });

    // Forgot link (demo only)
    $('#forgotLink').addEventListener('click', e => {
      e.preventDefault();
      alert('In production, this would email you a reset link.');
    });

    // Inline Create Account (no third page)
    const sPass = $('#s-pass'), sConfirm = $('#s-confirm'), sEmail = $('#s-email'), sName = $('#s-name'), sTerms = $('#s-terms');
    const meter = $('#strength'), createBtn = $('#createBtn'), createMsg = $('#createMsg');

    const toggleBtn = (btnSel, inputEl) => {
      $(btnSel).addEventListener('click', (e) => {
        const isText = inputEl.type === 'text';
        inputEl.type = isText ? 'password' : 'text';
        e.target.textContent = isText ? 'Show' : 'Hide';
        e.target.setAttribute('aria-pressed', String(!isText));
      });
    };
    toggleBtn('#toggleNew', sPass);
    toggleBtn('#toggleConfirm', sConfirm);

    function scorePassword(p){
      let s = 0; if (p.length>=8) s++; if (/[0-9]/.test(p)&&/[A-Za-z]/.test(p)) s++; if (/[^A-Za-z0-9]/.test(p)) s++; return Math.min(3, s);
    }
    function paintStrength(p){
      const lvl = scorePassword(p);
      meter.dataset.level = String(lvl);
      meter.firstElementChild.style.background = ['#e5e7eb','#facc15','#22c55e','#16a34a'][lvl];
    }
    sPass.addEventListener('input', e => paintStrength(e.target.value));

    createBtn.addEventListener('click', () => {
      createMsg.textContent = '';
      if (!sName.value.trim()) return createMsg.textContent = 'Enter your name.';
      if (!emailRe.test(sEmail.value.trim())) return createMsg.textContent = 'Enter a valid university email.';
      if (sPass.value.length < 8) return createMsg.textContent = 'Password must be at least 8 characters.';
      if (sPass.value !== sConfirm.value) return createMsg.textContent = 'Passwords do not match.';
      if (!sTerms.checked) return createMsg.textContent = 'Please accept the Terms & Privacy Policy.';
      createMsg.textContent = 'Account created! Redirecting…';
      setTimeout(()=>{ window.location.href = 'index.html#app'; }, 700);
    });

    // Initialize meter
    paintStrength('');
  </script>
</body>
</html><!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>ParkPal — Smart Parking for Zayed University</title>
  <meta name="description" content="ParkPal — Smart Parking app concept for Zayed University: real-time availability, reservations, and guided directions.">
  <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
  <style>
    :root{ --accent:#c1121f; --accent-light:#ff4d4d; --muted:#6b7280; --glass:rgba(255,255,255,0.06) }
    *{box-sizing:border-box}
    body{ font-family:Inter,system-ui,-apple-system,'Segoe UI',Roboto,'Helvetica Neue',Arial; margin:0;
      background:linear-gradient(180deg,#fff8f8,#ffeaea); color:#0f1724 }
    .topbar{background:var(--accent);color:white;text-align:center;padding:6px 0;font-size:14px;font-weight:500}
    .container{max-width:1100px;margin:36px auto;padding:24px}
    header{display:flex;align-items:center;justify-content:space-between}
    .brand{display:flex;gap:14px;align-items:center}
    .logo{display:flex;align-items:center;gap:6px;background:linear-gradient(135deg,var(--accent),var(--accent-light));
      color:white;border-radius:12px;padding:8px 12px;font-weight:700;font-size:18px;box-shadow:0 4px 10px rgba(193,18,31,0.3)}
    h1{margin:0;font-size:28px}
    p.lead{color:var(--muted);margin-top:6px}
    .hero{display:grid;grid-template-columns:1fr 420px;gap:28px;margin-top:22px;align-items:center}
    .card{background:white;border-radius:14px;padding:18px;box-shadow:0 6px 20px rgba(193,18,31,0.08)}
    .features{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:18px}
    .feature{padding:12px;border-radius:10px;background:var(--glass);border:1px solid rgba(15,23,36,0.04)}
    .app-mock{padding:14px;border-radius:12px;background:linear-gradient(180deg,#ffffff,#fff3f3);height:520px;width:100%;display:flex;flex-direction:column}
    .map{flex:1;border-radius:10px;background:linear-gradient(180deg,#ffd9d9,#ffc3c3);display:flex;align-items:center;justify-content:center;font-weight:700;color:#7a0404;text-align:center;padding:10px}
    .spots{margin-top:14px;display:grid;grid-template-columns:repeat(4,1fr);gap:8px}
    .spot{padding:8px;border-radius:8px;text-align:center;font-weight:600;cursor:pointer}
    .spot.available{background:#dcfce7;color:#065f46}
    .spot.taken{background:#fee2e2;color:#991b1b}
    .spot.reserved{background:#fff7ed;color:#92400e}
    .controls{margin-top:12px;display:flex;gap:8px;align-items:center;flex-wrap:wrap}
    .btn{background:var(--accent);color:white;padding:10px 14px;border-radius:10px;border:0;cursor:pointer;transition:0.2s}
    .btn:hover{background:var(--accent-light)}
    .btn.ghost{background:transparent;color:var(--accent);border:1px solid rgba(193,18,31,0.3)}
    section{margin-top:26px}
    select.gate-select{padding:8px 12px;border-radius:8px;border:1px solid rgba(193,18,31,0.3);font-weight:500}
    footer{margin-top:28px;padding:18px;text-align:center;color:var(--muted)}
    @media (max-width:900px){.hero{grid-template-columns:1fr} .features{grid-template-columns:repeat(2,1fr)} .app-mock{height:420px}}
    @media (max-width:560px){.features{grid-template-columns:1fr} .spots{grid-template-columns:repeat(3,1fr)}}
  </style>
</head>
<body>
  <div class="topbar">Zayed University — Abu Dhabi campus</div>

  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">
          <span>P</span><i class="fas fa-car"></i><span>PARK</span><span>PAL</span>
        </div>
        <div>
          <h1>ParkPal</h1>
          <p class="lead">Smart Parking for Zayed University — live availability, reservation, and guided directions</p>
        </div>
      </div>
      <nav>
        <a class="btn ghost" href="login.html" style="margin-right:8px">Log in</a>
        <button class="btn" onclick="document.getElementById('app').scrollIntoView({behavior:'smooth'})">Open App</button>
        <a class="btn ghost" href="login.html" style="margin-left:8px">Log out</a>
      </nav>
    </header>

    <main>
      <div class="hero">
        <div>
          <div class="card">
            <h2>Problem &amp; Solution</h2>
            <p style="color:var(--muted)"><strong>ParkPal</strong> uses sensors and real-time data to show available bays, allow reservations, and guide drivers to their spot — reducing time wasted and improving circulation around campus.</p>

            <div class="features" style="margin-top:16px">
              <div class="feature"><strong>Real-time Availability</strong><div style="color:var(--muted);font-size:13px;margin-top:6px">Sensor-driven updates show which spaces are free right now.</div></div>
              <div class="feature"><strong>Reserve a Spot</strong><div style="color:var(--muted);font-size:13px;margin-top:6px">Book in advance to guarantee a space.</div></div>
              <div class="feature"><strong>Guided Directions</strong><div style="color:var(--muted);font-size:13px;margin-top:6px">Turn-by-turn guidance to your bay.</div></div>
            </div>

            <div style="margin-top:14px;display:flex;gap:8px">
              <button class="btn" onclick="document.getElementById('app').scrollIntoView({behavior:'smooth'})">Try Demo</button>
              <button class="btn ghost" onclick="alert('Request sent to campus IT for pilot program')">Request Pilot</button>
            </div>
          </div>

          <section>
            <h2>How it works</h2>
            <div class="how">
              <div class="card">
                <ol>
                  <li>Sensors detect occupancy and send data to the cloud.</li>
                  <li>Backend processes data and updates availability in real time.</li>
                  <li>Mobile app displays open spots; users can reserve and get directions.</li>
                </ol>
              </div>
              <div class="card">
                <strong>Tech stack (suggested)</strong>
                <ul style="color:var(--muted);margin-top:8px">
                  <li>IoT sensors (ultrasonic/magnetic)</li>
                  <li>MQTT/WebSockets for real-time updates</li>
                  <li>Cloud backend (Node.js / Python)</li>
                  <li>Mobile app (React Native / PWA)</li>
                </ul>
              </div>
            </div>
          </section>

          <section>
            <h2>Pilot plan</h2>
            <div class="card">
              <p style="color:var(--muted)">Start with one parking lot near the main campus entrance: instrument 30 spaces, run a 4-week pilot, measure search-time reduction and satisfaction, then scale.</p>
            </div>
          </section>
        </div>

        <!-- APP MOCK -->
        <aside id="app" class="card app-mock">
          <div style="display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:6px">
            <div>
              <strong>App Preview</strong>
              <div style="font-size:12px;color:var(--muted)">ParkPal — Live Lot</div>
            </div>
            <div>
              <label for="gateSelect" style="font-size:13px;color:var(--muted);margin-right:4px;">Gate:</label>
              <select id="gateSelect" class="gate-select" onchange="changeGate(this.value)">
                <option value="1">Gate 1</option><option value="2">Gate 2</option><option value="3">Gate 3</option>
                <option value="4">Gate 4</option><option value="5">Gate 5</option><option value="6">Gate 6</option>
                <option value="7">Gate 7</option><option value="8">Gate 8</option><option value="9">Gate 9</option>
              </select>
            </div>
            <div style="font-size:12px;color:var(--muted)">Status: <span id="statusText">Connected</span></div>
          </div>

          <div class="map" id="mapArea">Map placeholder — Select a gate to view bays</div>
          <div class="spots" id="spotsGrid"></div>

          <div class="controls">
            <button class="btn" onclick="reserveBest()">Reserve Nearest</button>
            <button class="btn ghost" onclick="simulateToggle()">Simulate Change</button>
            <div style="margin-left:auto;color:var(--muted);font-size:13px">Next update: <span id="nextUpdate">--</span></div>
          </div>
        </aside>
      </div>

      <section>
        <h2>Accessibility & Privacy</h2>
        <div class="card">
          <p style="color:var(--muted)">We collect minimal data for reservations and directions. Accessibility includes voice guidance and high-contrast modes.</p>
        </div>
      </section>

      <section>
        <h2>Project Team</h2>
        <div class="card">
          <ul style="color:var(--muted);margin:0">
            <li><strong>Zayed Ibrahim Alawadhi</strong> — Concept & UX Design</li>
            <li><strong>Sultan Alsuwaidi</strong> — Frontend Development</li>
            <li><strong>Mohammed Alhmeiri</strong> — IoT & Sensor Integration</li>
            <li><strong>Mohammed Alawadhi</strong> — Research & Data Analysis</li>
          </ul>
        </div>
      </section>
    </main>

    <footer>
       <div style="max-width:800px;margin:0 auto">
    <div style="display:flex;justify-content:space-between;gap:12px;align-items:center;flex-wrap:wrap">
      <div>ParkPal &copy; <span id="year"></span> — Zayed University Concept</div>
      <div style="color:var(--muted)">Built for campus pilots • Contact: campus-it@zayedu.ac.ae</div>
    </div>

    <!-- NEW: Technical support line -->
    <div style="margin-top:10px;text-align:center;color:var(--muted);font-size:14px">
      Technical support: <a href="mailto:zzayd199@gmail.com">zzayd199@gmail.com</a>
    </div>
  </div>
  </div>

  <script>
    const yearEl = document.getElementById('year');
    const grid = document.getElementById('spotsGrid');
    const map = document.getElementById('mapArea');
    const nextEl = document.getElementById('nextUpdate');
    yearEl.textContent = new Date().getFullYear();

    const gates = {};
    for (let g = 1; g <= 9; g++) {
      gates[g] = Array.from({ length: 16 }, (_, i) => ({
        id: i + 1,
        state: Math.random() > 0.6 ? 'available' : 'taken'
      }));
    }

    let currentGate = 1;
    const spots = () => gates[currentGate];

    function render() {
      grid.innerHTML = '';
      const data = spots();
      data.forEach(s => {
        const el = document.createElement('div');
        el.className = 'spot ' + (s.state === 'available' ? 'available' : s.state === 'reserved' ? 'reserved' : 'taken');
        el.textContent = `Bay ${s.id}`;
        el.onclick = () => toggleReserve(s.id);
        grid.appendChild(el);
      });
      const free = data.filter(s => s.state === 'available').length;
      map.textContent = `Gate ${currentGate}: ${free} spots available`;
    }

    function toggleReserve(id) {
      const s = spots().find(x => x.id === id);
      if (!s) return;
      if (s.state === 'available') {
        s.state = 'reserved';
        alert(`You reserved Bay ${id} at Gate ${currentGate}.`);
      } else if (s.state === 'reserved') {
        s.state = 'available';
        alert(`Reservation for Bay ${id} at Gate ${currentGate} cancelled.`);
      } else {
        alert('Bay is occupied. Try another.');
      }
      render();
    }

    function reserveBest() {
      const best = spots().find(s => s.state === 'available');
      if (!best) { alert('No available bays right now.'); return; }
      best.state = 'reserved';
      alert(`Reserved Bay ${best.id} at Gate ${currentGate}.\nGuiding you now...`);
      render();
      map.textContent = `Gate ${currentGate}: Reserved Bay ${best.id}`;
    }

    function simulateToggle() {
      const data = spots();
      for (let i = 0; i < 3; i++) {
        const idx = Math.floor(Math.random() * data.length);
        data[idx].state = (data[idx].state === 'taken') ? 'available' : 'taken';
      }
      render();
    }

    function changeGate(gateNum) {
      currentGate = parseInt(gateNum,10);
      render();
    }

    function tick() {
      nextEl.textContent = new Date(Date.now() + 5000).toLocaleTimeString();
      if (Math.random() < 0.4) simulateToggle();
    }

    setInterval(tick, 5000);
    render();
    tick();

    document.addEventListener('keydown', e => {
      if (e.key === 'r') reserveBest();
      if (e.key === 's') simulateToggle();
    });
  </script>
</body>
</html

