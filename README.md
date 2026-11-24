<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EcoPoints — Earn & Cash Out via GCash</title>
  <style>
    :root { --primary: #1b7a43; --gcash: #007dfe; --admin: #0f172a; --bg: #f3f8f4; --card: #ffffff; --text: #1e293b; --danger: #dc2626; }
    body { font-family: system-ui, sans-serif; background: var(--bg); color: var(--text); margin: 0; padding: 20px; }
    .container { max-width: 820px; margin: 0 auto; }
    .auth-box { max-width: 380px; margin: 60px auto; background: var(--card); padding: 28px; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.08); }
    input, select { width: 100%; padding: 10px; margin: 8px 0; border: 1px solid #cbd5e1; border-radius: 6px; box-sizing: border-box; font-size: 0.95rem; }
    header { background: var(--primary); color: white; padding: 24px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; }
    header.admin-header { background: var(--admin); }
    .points-badge { font-size: 1.7rem; font-weight: bold; background: rgba(255,255,255,0.2); padding: 8px 16px; border-radius: 8px; }
    .peso-value { font-size: 0.9rem; margin-top: 4px; opacity: 0.95; }
    .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 20px; }
    .card { background: var(--card); padding: 20px; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.06); margin-top: 20px; }
    .grid .card { margin-top: 0; }
    button { background: var(--primary); color: white; border: none; padding: 11px 14px; border-radius: 6px; cursor: pointer; font-weight: 600; width: 100%; margin-top: 8px; font-size: 0.95rem; }
    button:hover { opacity: 0.92; }
    button.gcash-btn { background: var(--gcash); }
    button.secondary { background: #64748b; }
    button.danger { background: var(--danger); }
    button.small-btn { width: auto; padding: 7px 12px; font-size: 0.82rem; margin-top: 0; }
    .hidden { display: none; }
    .rate-tag { background: #e0f2fe; color: #0369a1; padding: 6px 10px; border-radius: 6px; font-size: 0.85rem; font-weight: 600; display: inline-block; margin-bottom: 10px; }
    .upload-box { border: 2px dashed #94a3b8; border-radius: 8px; padding: 12px; text-align: center; background: #f8fafc; margin: 8px 0; cursor: pointer; }
    .upload-box:hover { border-color: var(--primary); background: #f0fdf4; }
    #photo-preview { max-width: 100%; max-height: 150px; border-radius: 6px; margin-top: 8px; display: none; object-fit: cover; }
    .history-list { list-style: none; padding: 0; margin: 0; }
    .history-item { display: flex; align-items: center; justify-content: space-between; gap: 12px; padding: 10px 0; border-bottom: 1px solid #e2e8f0; font-size: 0.9rem; color: #334155; flex-wrap: wrap; }
    .history-item:last-child { border-bottom: none; }
    .history-left { display: flex; align-items: center; gap: 12px; flex: 1; min-width: 220px; }
    .evidence-thumb { width: 60px; height: 60px; border-radius: 6px; object-fit: cover; border: 1px solid #cbd5e1; flex-shrink: 0; }
    .status-pending { color: #b45309; background: #fef3c7; padding: 2px 8px; border-radius: 999px; font-size: 0.78rem; font-weight: 600; }
    .status-approved { color: #15803d; background: #dcfce7; padding: 2px 8px; border-radius: 999px; font-size: 0.78rem; font-weight: 600; }
    .status-rejected { color: #b91c1c; background: #fee2e2; padding: 2px 8px; border-radius: 999px; font-size: 0.78rem; font-weight: 600; }
    @media (max-width: 640px) { .grid { grid-template-columns: 1fr; } }
  </style>
</head>
<body>

  <!-- LOG IN / SIGN UP SCREEN (USER OR ADMIN) -->
  <div id="auth-screen" class="auth-box">
    <h2 style="margin-top:0; color:var(--primary);">🌱 EcoPoints</h2>
    <p id="auth-subtitle" style="color:#64748b; font-size:0.9rem;">Mag-log in gamit ang User o Admin account.</p>
    <input type="text" id="name-input" class="hidden" placeholder="Full Name (hal. Maria Eloisa)" />
    <input type="email" id="email-input" placeholder="Email Address" />
    <input type="password" id="password-input" placeholder="Password" />
    <button id="auth-submit-btn">Log In</button>
    <button id="toggle-auth-btn" class="secondary">Wala pang account? Sign Up</button>
    <p id="auth-error" style="color:#dc2626; font-size:0.85rem; margin-top:10px;"></p>
  </div>

  <!-- USER DASHBOARD -->
  <div id="user-screen" class="container hidden">
    <header>
      <div>
        <h1 style="margin:0;">🌱 EcoPoints</h1>
        <p style="margin:4px 0 0; opacity:0.9;">Welcome, <span id="user-name">User</span>!</p>
      </div>
      <div style="text-align:right;">
        <div class="points-badge"><span id="balance">0</span> pts</div>
        <div class="peso-value">Katumbas: <strong>₱<span id="peso-balance">0.00</span></strong></div>
        <button class="logout-btn" style="background:rgba(0,0,0,0.25); padding:5px 10px; font-size:0.8rem; margin-top:6px;">Log Out</button>
      </div>
    </header>

    <div class="grid">
      <!-- SUBMIT BASURA WITH PHOTO EVIDENCE -->
      <div class="card">
        <h3 style="margin-top:0;">📸 Mag-submit ng Basura (+Points)</h3>

        <label style="font-size:0.85rem; font-weight:600;">1. Uri ng Basura / Eco-Action:</label>
        <select id="trash-type">
          <option value="Plastic Bottles / PET (1 kg)|500">🧴 Plastic Bottles / PET (1 kg) (+500 pts)</option>
          <option value="Aluminum Cans / Lata|20">🥫 Aluminum Cans / Lata (+20 pts)</option>
          <option value="Tanso / Copper (1 kg)|100000">🔌 Tanso / Copper (1 kg) (+100,000 pts)</option>
          <option value="Plastic Bottles (1 kg)|4">🥤 Plastic Bottles (1 kg) (+4 pts)</option>
          <option value="Bakal / Metal / Steel (1 kg)|500">⛓️ Bakal / Metal / Steel (1 kg) (+500 pts)</option>
        </select>

        <label style="font-size:0.85rem; font-weight:600;">2. Picture ng Basura (Required Evidence):</label>
        <div class="upload-box" onclick="document.getElementById('trash-photo').click()">
          <span id="upload-label" style="font-size:0.88rem; color:#475569;">📷 I-click para kumuha o pumili ng picture</span>
          <input type="file" id="trash-photo" accept="image/*" capture="environment" class="hidden" onchange="previewPhoto(event)" />
          <img id="photo-preview" alt="Preview ng basura" />
        </div>

        <button onclick="submitTrashWithPhoto()">Submit Evidence for Review</button>
        <p id="submit-msg" style="font-size:0.85rem; margin-top:8px;"></p>
      </div>

      <!-- GCASH CASHOUT -->
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

    <!-- ACTIVITY & EVIDENCE HISTORY -->
    <div class="card">
      <h3 style="margin-top:0;">Activity History & Photo Evidence</h3>
      <ul id="history" class="history-list"></ul>
    </div>
  </div>

  <!-- ADMIN DASHBOARD -->
  <div id="admin-screen" class="container hidden">
    <header class="admin-header">
      <div>
        <h1 style="margin:0;">🛡️ EcoPoints Admin</h1>
        <p style="margin:4px 0 0; opacity:0.85;">Logged in as <span id="admin-name">Admin</span></p>
      </div>
      <div style="text-align:right;">
        <button class="logout-btn" style="background:rgba(255,255,255,0.18); padding:7px 12px; font-size:0.85rem; margin-top:0;">Log Out</button>
      </div>
    </header>

    <div class="card">
      <h3 style="margin-top:0;">📸 Pending Photo Evidence</h3>
      <ul id="admin-pending-list" class="history-list"></ul>
    </div>

    <div class="card">
      <h3 style="margin-top:0;">👥 Registered Users</h3>
      <ul id="admin-users-list" class="history-list"></ul>
    </div>
  </div>

  <script>
    const PESO_PER_POINT = 0.10;
    const ADMIN_ACCOUNT = {
      email: "admin@ecopoints.ph",
      password: "admin123",
      name: "System Admin"
    };

    let isSignUp = false;
    let users = JSON.parse(localStorage.getItem("ecoUsers")) || {};
    let currentSession = JSON.parse(localStorage.getItem("ecoSession")) || null;
    let currentCompressedPhoto = null;

    const authScreen = document.getElementById("auth-screen");
    const userScreen = document.getElementById("user-screen");
    const adminScreen = document.getElementById("admin-screen");
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
        ? "Gumawa ng bagong User account."
        : "Mag-log in gamit ang User o Admin account.";
      authError.textContent = "";
    };

    authSubmitBtn.onclick = () => {
      const email = emailInput.value.trim().toLowerCase();
      const password = passwordInput.value;
      const name = nameInput.value.trim() || email.split("@")[0];
      authError.textContent = "";

      if (!email || !password) {
        authError.textContent = "Ilagay ang email at password.";
        return;
      }

      if (isSignUp) {
        if (email === ADMIN_ACCOUNT.email) {
          authError.textContent = "Hindi pwedeng i-register ang Admin email.";
          return;
        }
        if (users[email]) {
          authError.textContent = "May account na ang email na ito.";
          return;
        }
        users[email] = { name, password, points: 0, logs: [] };
        localStorage.setItem("ecoUsers", JSON.stringify(users));
        currentSession = { role: "user", email };
        localStorage.setItem("ecoSession", JSON.stringify(currentSession));
        routeSession();
        return;
      }

      // Check Admin credentials first
      if (email === ADMIN_ACCOUNT.email && password === ADMIN_ACCOUNT.password) {
        currentSession = { role: "admin", email: ADMIN_ACCOUNT.email, name: ADMIN_ACCOUNT.name };
        localStorage.setItem("ecoSession", JSON.stringify(currentSession));
        routeSession();
        return;
      }

      // Check Regular User credentials
      users = JSON.parse(localStorage.getItem("ecoUsers")) || {};
      if (!users[email] || users[email].password !== password) {
        authError.textContent = "Maling email o password. Mag-Sign Up muna kung wala pang account.";
        return;
      }

      currentSession = { role: "user", email };
      localStorage.setItem("ecoSession", JSON.stringify(currentSession));
      routeSession();
    };

    document.querySelectorAll(".logout-btn").forEach(btn => {
      btn.onclick = () => {
        currentSession = null;
        localStorage.removeItem("ecoSession");
        userScreen.classList.add("hidden");
        adminScreen.classList.add("hidden");
        authScreen.classList.remove("hidden");
        emailInput.
