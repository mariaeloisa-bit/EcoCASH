<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EcoPoints — Earn & Cash Out via GCash</title>
  <style>
    :root { --primary: #1b7a43; --gcash: #007dfe; --bg: #f3f8f4; --card: #ffffff; --text: #1e293b; }
    body { font-family: system-ui, sans-serif; background: var(--bg); color: var(--text); margin: 0; padding: 20px; }
    .container { max-width: 760px; margin: 0 auto; }
    .auth-box { max-width: 380px; margin: 60px auto; background: var(--card); padding: 28px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.08); }
    input, select { width: 100%; padding: 10px; margin: 8px 0; border: 1px solid #cbd5e1; border-radius: 6px; box-sizing: border-box; font-size: 0.95rem; }
    header { background: var(--primary); color: white; padding: 24px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; }
    .points-badge { font-size: 1.7rem; font-weight: bold; background: rgba(255,255,255,0.2); padding: 8px 16px; border-radius: 8px; }
    .peso-value { font-size: 0.9rem; margin-top: 4px; opacity: 0.95; }
    .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 20px; }
    .card { background: var(--card); padding: 20px; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.06); }
    button { background: var(--primary); color: white; border: none; padding: 11px 14px; border-radius: 6px; cursor: pointer; font-weight: 600; width: 100%; margin-top: 8px; font-size: 0.95rem; }
    button:hover { opacity: 0.92; }
    button.gcash-btn { background: var(--gcash); }
    button.secondary { background: #64748b; }
    .hidden { display: none; }
    ul { padding-left: 18px; font-size: 0.9rem; color: #475569; line-height: 1.6; }
    .rate-tag { background: #e0f2fe; color: #0369a1; padding: 6px 10px; border-radius: 6px; font-size: 0.85rem; font-weight: 600; display: inline-block; margin-bottom: 10px; }
    @media (max-width: 640px) { .grid { grid-template-columns: 1fr; } }
  </style>
</head>
<body>

  <!-- LOG IN / SIGN UP SCREEN -->
  <div id="auth-screen" class="auth-box">
    <h2 style="margin-top:0; color:var(--primary);">🌱 EcoPoints</h2>
    <p id="auth-subtitle" style="color:#64748b; font-size:0.9rem;">Mag-log in para mag-ipon ng points at mag-cash out sa GCash.</p>
    <input type="text" id="name-input" class="hidden" placeholder="Full Name (hal. Maria Eloisa)" />
    <input type="email" id="email-input" placeholder="Email Address" />
    <input type="password" id="password-input" placeholder="Password" />
    <button id="auth-submit-btn">Log In</button>
    <button id="toggle-auth-btn" class="secondary">Wala pang account? Sign Up</button>
    <p id="auth-error" style="color:#dc2626; font-size:0.85rem; margin-top:10px;"></p>
  </div>

  <!-- MAIN APP DASHBOARD -->
  <div id="app-screen" class="container hidden">
    <header>
      <div>
        <h1 style="margin:0;">🌱 EcoPoints</h1>
        <p style="margin:4px 0 0; opacity:0.9;">Welcome, <span id="user-name">User</span>!</p>
      </div>
      <div style="text-align:right;">
        <div class="points-badge"><span id="balance">0</span> pts</div>
        <div class="peso-value">Katumbas: <strong>₱<span id="peso-balance">0.00</span></strong></div>
        <button id="logout-btn" style="background:rgba(0,0,0,0.25); padding:5px 10px; font-size:0.8rem; margin-top:6px;">Log Out</button>
      </div>
    </header>

    <div class="grid">
      <div class="card">
        <h3 style="margin-top:0;">Mag-ipon ng EcoPoints</h3>
        <button onclick="earnPoints('Nag-recycle ng plastic/bote', 20)">♻️ Recycle Plastics/Cans (+20 pts)</button>
        <button onclick="earnPoints('Gumamit ng reusable tumbler/ecobag', 15)">🥤 Reusable Tumbler/Bag (+15 pts)</button>
        <button onclick="earnPoints('Naglakad o nag-bike papunta sa destination', 30)">🚲 Walk / Bike Commute (+30 pts)</button>
        <button onclick="earnPoints('Nagtanim ng puno/halaman', 100)">🌳 Plant a Seedling (+100 pts)</button>
      </div>

      <div class="card">
        <h3 style="margin-top:0; color:var(--gcash);">💙 Convert Points to GCash</h3>
        <div class="rate-tag">Rate: 100 pts = ₱10.00 GCash</div>
        
        <label style="font-size:0.85rem; font-weight:600;">Piliin ang Amount:</label>
        <select id="cashout-tier">
          <option value="100">100 pts → ₱10.00 GCash</option>
          <option value="200">200 pts → ₱20.00 GCash</option>
          <option value="500">500 pts → ₱50.00 GCash</option>
          <option value="1000">1,000 pts → ₱100.00 GCash</option>
        </select>

        <input type="tel" id="gcash-number" placeholder="GCash Number (hal. 09171234567)" maxlength="11" />
        <input type="text" id="gcash-name" placeholder="GCash Account Name (hal. Maria E.)" />
        
        <button class="gcash-btn" onclick="requestGCashCashout()">Cash Out to GCash</button>
        <p id="cashout-msg" style="font-size:0.85rem; margin-top:8px;"></p>
      </div>
    </div>

    <div class="card" style="margin-top: 20px;">
      <h3 style="margin-top:0;">Activity & GCash Cashout History</h3>
      <ul id="history"></ul>
    </div>
  </div>

  <script>
    const PESO_PER_POINT = 0.10;
    let isSignUp = false;
    let users = JSON.parse(localStorage.getItem("ecoUsers")) || {};
    let currentEmail = localStorage.getItem("ecoCurrentUser") || null;

    const authScreen = document.getElementById("auth-screen");
    const appScreen = document.getElementById("app-screen");
    const nameInput = document.getElementById("name-input");
    const emailInput = document.getElementById("email-input");
    const passwordInput = document.getElementById("password-input");
    const authSubmitBtn = document.getElementById("auth-submit-btn");
    const toggleAuthBtn = document.getElementById("toggle-auth-btn");
    const authError = document.getElementById("auth-error");

    toggleAuthBtn.onclick = () => {
      isSignUp = !isSignUp;
      nameInput.classList.toggle("hidden", !isSignUp);
      authSubmitBtn.textContent = isSignUp ? "Create Account" : "Log In";
      toggleAuthBtn.textContent = isSignUp ? "May account na? Log In" : "Wala pang account? Sign Up";
      document.getElementById("auth-subtitle").textContent = isSignUp
        ? "Gumawa ng bagong EcoPoints account."
        : "Mag-log in para mag-ipon ng points at mag-cash out sa GCash.";
      authError.textContent = "";
    };

    authSubmitBtn.onclick = () => {
      const email = emailInput.value.trim().toLowerCase();
      const password = passwordInput.value;
      const name = nameInput.value.trim() || email.split("@")[0];
      authError.textContent = "";

      if (!email || !password) {
        return (authError.textContent = "Ilagay ang email at password.");
      }

      if (isSignUp) {
        if (users[email]) return (authError.textContent = "May account na ang email na ito.");
        users[email] = { name, password, points: 0, logs: [] };
        localStorage.setItem("ecoUsers", JSON.stringify(users));
        currentEmail = email;
        localStorage.setItem("ecoCurrentUser", currentEmail);
        showDashboard();
      } else {
        if (!users[email] || users[email].password !== password) {
          return (authError.textContent = "Maling email o password. Mag-Sign Up muna kung wala pang account.");
        }
        currentEmail = email;
        localStorage.setItem("ecoCurrentUser", currentEmail);
        showDashboard();
      }
    };

    document.getElementById("logout-btn").onclick = () => {
      currentEmail = null;
      localStorage.removeItem("ecoCurrentUser");
      authScreen.classList.remove("hidden");
      appScreen.classList.add("hidden");
    };

    function showDashboard() {
      const user = users[currentEmail];
      if (!user) return;
      document.getElementById("user-name").textContent = user.name;
      document.getElementById("balance").textContent = user.points;
      document.getElementById("peso-balance").textContent = (user.points * PESO_PER_POINT).toFixed(2);
      document.getElementById("history").innerHTML =
        user.logs.map(item => `<li>${item}</li>`).join("") || "<li>Wala pang activity. Mag-ipon ng points sa itaas!</li>";
      authScreen.classList.add("hidden");
      appScreen.classList.remove("hidden");
    }

    function saveData() {
      localStorage.setItem("ecoUsers", JSON.stringify(users));
      showDashboard();
    }

    window.earnPoints = (action, amount) => {
      const user = users[currentEmail];
      user.points += amount;
      user.logs.unshift(`+${amount} pts — ${action} (${new Date().toLocaleDateString()})`);
      saveData();
    };

    window.requestGCashCashout = () => {
      const user = users[currentEmail];
      const ptsRequired = Number(document.getElementById("cashout-tier").value);
      const pesoAmount = ptsRequired * PESO_PER_POINT;
      const gcashNumber = document.getElementById("gcash-number").value.trim();
      const gcashName = document.getElementById("gcash-name").value.trim();
      const msg = document.getElementById("cashout-msg");

      msg.style.color = "#dc2626";
      if (user.points < ptsRequired) return (msg.textContent = `Kulang pa ang points mo. Kailangan ng ${ptsRequired} pts.`);
      if (!/^09\d{9}$/.test(gcashNumber)) return (msg.textContent = "Ilagay ang tamang 11-digit GCash number (09xxxxxxxxx).");
      if (!gcashName) return (msg.textContent = "Ilagay ang pangalan ng GCash account.");

      user.points -= ptsRequired;
      user.logs.unshift(`-${ptsRequired} pts — GCash Cashout ₱${pesoAmount.toFixed(2)} to ${gcashNumber} (${gcashName}) [Pending]`);
      saveData();

      document.getElementById("gcash-number").value = "";
      document.getElementById("gcash-name").value = "";
      msg.style.color = "#15803d";
      msg.textContent = `Naipadala na ang request mo na ₱${pesoAmount.toFixed(2)} sa GCash (${gcashNumber})!`;
    };

    if (currentEmail && users[currentEmail]) showDashboard();
  </script>
</body>
</html>
