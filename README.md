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
    .hidden { display: none !important; }
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
    <button type="button" id="auth-submit-btn" onclick="handleAuthSubmit()">Log In</button>
    <button type="button" id="toggle-auth-btn" class="secondary" onclick="toggleAuthMode()">Wala pang account? Sign Up</button>
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
        <button type="button" onclick="logoutUser()" style="background:rgba(0,0,0,0.25); padding:5px 10px; font-size:0.8rem; margin-top:6px;">Log Out</button>
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

        <button type="button" onclick="submitTrashWithPhoto()">Submit Evidence for Review</button>
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

        <button type="button" class="gcash-btn" onclick="requestGCashCashout()">Cash Out to GCash</button>
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
        <p style="margin:4px 0 0; opacity:0.85;">Logged in as <span id="admin-name">System Admin</span></p>
      </div>
      <div style="text-align:right;">
        <button type="button" onclick="logoutUser()" style="background:rgba(255,255,255,0.18); padding:7px 12px; font-size:0.85rem; margin-top:0;">Log Out</button>
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
      email: "eloisajeff14@gmail.com",
      password: "091420251217",
      name: "System Admin"
    };

    let isSignUp = false;
    let users = {};
    let currentSession = null;
    let currentCompressedPhoto = null;

    try {
      users = JSON.parse(localStorage.getItem("ecoUsers")) || {};
      currentSession = JSON.parse(localStorage.getItem("ecoSession")) || null;
    } catch (e) {
      users = {};
      currentSession = null;
    }

    function toggleAuthMode() {
      isSignUp = !isSignUp;
      const nameInput = document.getElementById("name-input");
      const submitBtn = document.getElementById("auth-submit-btn");
      const toggleBtn = document.getElementById("toggle-auth-btn");
      const subtitle = document.getElementById("auth-subtitle");
      const errorBox = document.getElementById("auth-error");

      if (isSignUp) {
        nameInput.classList.remove("hidden");
        submitBtn.textContent = "Create Account";
        toggleBtn.textContent = "May account na? Log In";
        subtitle.textContent = "Gumawa ng bagong User account.";
      } else {
        nameInput.classList.add("hidden");
        submitBtn.textContent = "Log In";
        toggleBtn.textContent = "Wala pang account? Sign Up";
        subtitle.textContent = "Mag-log in gamit ang User o Admin account.";
      }
      errorBox.textContent = "";
    }

    function handleAuthSubmit() {
      const nameInput = document.getElementById("name-input");
      const emailInput = document.getElementById("email-input");
      const passwordInput = document.getElementById("password-input");
      const authError = document.getElementById("auth-error");

      const email = emailInput.value.trim().toLowerCase();
      const password = passwordInput.value;
      const name = nameInput.value.trim() || email.split("@")[0];
      authError.textContent = "";

      if (!email || !password) {
        authError.textContent = "Ilagay ang email at password.";
        return;
      }

      if (isSignUp) {
        if (email === ADMIN_ACCOUNT.email.toLowerCase()) {
          authError.textContent = "Hindi pwedeng i-register ang Admin email.";
          return;
        }
        if (users[email]) {
          authError.textContent = "May account na ang email na ito.";
          return;
        }
        users[email] = { name: name, password: password, points: 0, logs: [] };
        localStorage.setItem("ecoUsers", JSON.stringify(users));
        currentSession = { role: "user", email: email };
        localStorage.setItem("ecoSession", JSON.stringify(currentSession));
        routeSession();
        return;
      }

      if (email === ADMIN_ACCOUNT.email.toLowerCase() && password === ADMIN_ACCOUNT.password) {
        currentSession = { role: "admin", email: ADMIN_ACCOUNT.email, name: ADMIN_ACCOUNT.name };
        localStorage.setItem("ecoSession", JSON.stringify(currentSession));
        routeSession();
        return;
      }

      users = JSON.parse(localStorage.getItem("ecoUsers")) || {};
      if (!users[email] || users[email].password !== password) {
        authError.textContent = "Maling email o password. Mag-Sign Up muna kung wala pang account.";
        return;
      }

      currentSession = { role: "user", email: email };
      localStorage.setItem("ecoSession", JSON.stringify(currentSession));
      routeSession();
    }

    function logoutUser() {
      currentSession = null;
      localStorage.removeItem("ecoSession");
      document.getElementById("user-screen").classList.add("hidden");
      document.getElementById("admin-screen").classList.add("hidden");
      document.getElementById("auth-screen").classList.remove("hidden");
      document.getElementById("email-input").value = "";
      document.getElementById("password-input").value = "";
    }

    function previewPhoto(event) {
      const file = event.target.files[0];
      if (!file) return;

      const reader = new FileReader();
      reader.onload = function(e) {
        const img = new Image();
        img.onload = function() {
          const canvas = document.createElement("canvas");
          const maxWidth = 300;
          const scale = maxWidth / img.width;
          canvas.width = maxWidth;
          canvas.height = Math.max(1, img.height * scale);
          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, canvas.width, canvas.height);

          currentCompressedPhoto = canvas.toDataURL("image/jpeg", 0.7);
          const preview = document.getElementById("photo-preview");
          preview.src = currentCompressedPhoto;
          preview.style.display = "block";
          document.getElementById("upload-label").textContent = "✅ Picture ready! (I-click ulit kung papalitan)";
        };
        img.src = e.target.result;
      };
      reader.readAsDataURL(file);
    }

    function submitTrashWithPhoto() {
      const msg = document.getElementById("submit-msg");
      msg.style.color = "#dc2626";

      if (!currentCompressedPhoto) {
        msg.textContent = "⚠️ Kailangan muna mag-upload o mag-picture ng basura bago mag-submit!";
        return;
      }

      users = JSON.parse(localStorage.getItem("ecoUsers")) || users;
      const parts = document.getElementById("trash-type").value.split("|");
      const actionLabel = parts[0];
      const pts = Number(String(parts[1]).replace(/,/g, "")) || 0;
      const user = users[currentSession.email];

      const entryId = "ev_" + Date.now() + "_" + Math.random().toString(36).slice(2, 6);
      user.logs.unshift({
        id: entryId,
        type: "evidence",
        status: "pending",
        pts: pts,
        actionLabel: actionLabel,
        date: new Date().toLocaleDateString(),
        text: actionLabel + " (" + pts.toLocaleString() + " pts) — " + new Date().toLocaleDateString(),
        photo: currentCompressedPhoto
      });

      currentCompressedPhoto = null;
      document.getElementById("trash-photo").value = "";
      document.getElementById("photo-preview").style.display = "none";
      document.getElementById("upload-label").textContent = "📷 I-click para kumuha o pumili ng picture";

      msg.style.color = "#15803d";
      msg.textContent = "Naisumite ang picture! Magkakaroon ng +" + pts.toLocaleString() + " pts kapag na-approve ng Admin.";
      saveUsersAndRefresh();
    }

    function reviewEvidence(userEmail, entryId, decision) {
      users = JSON.parse(localStorage.getItem("ecoUsers")) || users;
      const targetUser = users[userEmail];
      if (!targetUser) return;
      const item = (targetUser.logs || []).find(function(log) { return log && log.id === entryId; });
      if (!item || item.status !== "pending") return;

      if (decision === "approve") {
        item.status = "approved";
        targetUser.points = (Number(targetUser.points) || 0) + (Number(item.pts) || 0);
        item.text = "+" + Number(item.pts).toLocaleString() + " pts — " + item.actionLabel + " (" + item.date + ")";
      } else {
        item.status = "rejected";
        item.text = "0 pts — " + item.actionLabel + " (" + item.date + ") [Rejected]";
      }

      saveUsersAndRefresh();
    }

    function getStatusBadge(item) {
      if (!item || item.type !== "evidence") return "";
      if (item.status === "approved") return '<span class="status-approved">Approved</span>';
      if (item.status === "rejected") return '<span class="status-rejected">Rejected</span>';
      return '<span class="status-pending">Pending Review</span>';
    }

    function showUserDashboard() {
      users = JSON.parse(localStorage.getItem("ecoUsers")) || users;
      const user = users[currentSession.email];
      if (!user) return;

      const safePoints = Number(user.points) || 0;
      document.getElementById("user-name").textContent = user.name;
      document.getElementById("balance").textContent = safePoints.toLocaleString();
      document.getElementById("peso-balance").textContent = (safePoints * PESO_PER_POINT).toFixed(2);

      const historyEl = document.getElementById("history");
      if (!user.logs.length) {
        historyEl.innerHTML = "<li style='color:#64748b; font-size:0.9rem;'>Wala pang activity. Mag-picture ng basura para mag-ipon ng points!</li>";
      } else {
        historyEl.innerHTML = user.logs.map(function(item) {
          if (typeof item === "string") {
            return '<li class="history-item"><div class="history-left"><span>' + item + '</span></div></li>';
          }
          const imgHtml = item.photo ? '<img src="' + item.photo + '" class="evidence-thumb" alt="Evidence" />' : '';
          return '<li class="history-item"><div class="history-left">' + imgHtml + '<span>' + item.text + '</span></div>' + getStatusBadge(item) + '</li>';
        }).join("");
      }

      document.getElementById("auth-screen").classList.add("hidden");
      document.getElementById("admin-screen").classList.add("hidden");
      document.getElementById("user-screen").classList.remove("hidden");
    }

    function showAdminDashboard() {
      users = JSON.parse(localStorage.getItem("ecoUsers")) || users;
      document.getElementById("admin-name").textContent = currentSession.name || ADMIN_ACCOUNT.name;

      const pendingList = document.getElementById("admin-pending-list");
      const usersList = document.getElementById("admin-users-list");
      const pendingItems = [];

      Object.keys(users).forEach(function(email) {
        const u = users[email];
        (u.logs || []).forEach(function(item) {
          if (item && item.type === "evidence" && item.status === "pending") {
            pendingItems.push({ email: email, userName: u.name, item: item });
          }
        });
      });

      if (!pendingItems.length) {
        pendingList.innerHTML = "<li style='color:#64748b; font-size:0.9rem;'>Walang pending na picture para i-review ngayon.</li>";
      } else {
        pendingList.innerHTML = pendingItems.map(function(entry) {
          const imgHtml = entry.item.photo ? '<img src="' + entry.item.photo + '" class="evidence-thumb" alt="Evidence" />' : '';
          return '<li class="history-item"><div class="history-left">' + imgHtml +
            '<div><div><strong>' + entry.userName + '</strong> <span style="color:#64748b; font-size:0.85rem;">(' + entry.email + ')</span></div>' +
            '<div style="font-size:0.88rem; margin-top:2px;">' + entry.item.text + '</div></div></div>' +
            '<div style="display:flex; gap:8px;">' +
            '<button type="button" class="small-btn" onclick="reviewEvidence(\'' + entry.email + '\', \'' + entry.item.id + '\', \'approve\')">Approve</button>' +
            '<button type="button" class="small-btn danger" onclick="reviewEvidence(\'' + entry.email + '\', \'' + entry.item.id + '\', \'reject\')">Reject</button>' +
            '</div></li>';
        }).join("");
      }

      const emails = Object.keys(users);
      if (!emails.length) {
        usersList.innerHTML = "<li style='color:#64748b; font-size:0.9rem;'>Wala pang naka-register na user.</li>";
      } else {
        usersList.innerHTML = emails.map(function(email) {
          const u = users[email];
          const pts = Number(u.points) || 0;
          return '<li class="history-item"><div><strong>' + u.name + '</strong> <span style="color:#64748b; font-size:0.85rem;">(' + email + ')</span></div>' +
            '<div><strong>' + pts.toLocaleString() + ' pts</strong> <span style="color:#64748b; font-size:0.85rem;">(₱' + (pts * PESO_PER_POINT).toFixed(2) + ')</span></div></li>';
        }).join("");
      }

      document.getElementById("auth-screen").classList.add("hidden");
      document.getElementById("user-screen").classList.add("hidden");
      document.getElementById("admin-screen").classList.remove("hidden");
    }

    function saveUsersAndRefresh() {
      localStorage.setItem("ecoUsers", JSON.stringify(users));
      routeSession();
    }

    function routeSession() {
      if (!currentSession) return;
      if (currentSession.role === "admin") {
        showAdminDashboard();
      } else if (users[currentSession.email]) {
        showUserDashboard();
      }
    }

    function requestGCashCashout() {
      users = JSON.parse(localStorage.getItem("ecoUsers")) || users;
      const user = users[currentSession.email];
      const safePoints = Number(user.points) || 0;
      const ptsRequired = Number(document.getElementById("cashout-tier").value);
      const pesoAmount = ptsRequired * PESO_PER_POINT;
      const gcashNumber = document.getElementById("gcash-number").value.trim();
      const gcashName = document.getElementById("gcash-name").value.trim();
      const msg = document.getElementById("cashout-msg");

      msg.style.color = "#dc2626";
      if (safePoints < ptsRequired) {
        msg.textContent = "Kulang pa ang points mo. Kailangan ng " + ptsRequired.toLocaleString() + " pts.";
        return;
      }
      if (!/^09\d{9}$/.test(gcashNumber)) {
        msg.textContent = "Ilagay ang tamang 11-digit GCash number (09xxxxxxxxx).";
        return;
      }
      if (!gcashName) {
        msg.textContent = "Ilagay ang pangalan ng GCash account.";
        return;
      }

      user.points = safePoints - ptsRequired;
      user.logs.unshift({
        type: "cashout",
        text: "-" + ptsRequired.toLocaleString() + " pts — GCash Cashout ₱" + pesoAmount.toFixed(2) + " to " + gcashNumber + " (" + gcashName + ") [Pending]",
        photo: null
      });
      saveUsersAndRefresh();

      document.getElementById("gcash-number").value = "";
      document.getElementById("gcash-name").value = "";
      msg.style.color = "#15803d";
      msg.textContent = "Naipadala na ang request mo na ₱" + pesoAmount.toFixed(2) + " sa GCash (" + gcashNumber + ")!";
    }

    routeSession();
  </script>
</body>
</html>
