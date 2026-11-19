<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EcoPoints — Earn & Cash Out via GCash</title>
  <style>
    :root { --primary: #1b7a43; --gcash: #007dfe; --bg: #f3f8f4; --card: #ffffff; --text: #1e293b; --danger: #dc2626; }
    body { font-family: system-ui, sans-serif; background: var(--bg); color: var(--text); margin: 0; padding: 20px; }
    .container { max-width: 820px; margin: 0 auto; }
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
    button.danger { background: var(--danger); }
    button.small-btn { width: auto; padding: 6px 10px; font-size: 0.8rem; margin-top: 0; }
    .hidden { display: none; }
    .rate-tag { background: #e0f2fe; color: #0369a1; padding: 6px 10px; border-radius: 6px; font-size: 0.85rem; font-weight: 600; display: inline-block; margin-bottom: 10px; }
    .upload-box { border: 2px dashed #94a3b8; border-radius: 8px; padding: 12px; text-align: center; background: #f8fafc; margin: 8px 0; cursor: pointer; }
    .upload-box:hover { border-color: var(--primary); background: #f0fdf4; }
    #photo-preview { max-width: 100%; max-height: 150px; border-radius: 6px; margin-top: 8px; display: none; object-fit: cover; }
    .history-list { list-style: none; padding: 0; margin: 0; }
    .history-item { display: flex; align-items: center; justify-content: space-between; gap: 12px; padding: 10px 0; border-bottom: 1px solid #e2e8f0; font-size: 0.9rem; color: #334155; flex-wrap: wrap; }
    .history-item:last-child { border-bottom: none; }
    .history-left { display: flex; align-items: center; gap: 12px; flex: 1; min-width: 220px; }
    .evidence-thumb { width: 54px; height: 54px; border-radius: 6px; object-fit: cover; border: 1px solid #cbd5e1; flex-shrink: 0; }
    .status-pending { color: #b45309; background: #fef3c7; padding: 2px 8px; border-radius: 999px; font-size: 0.78rem; font-weight: 600; }
    .status-approved { color: #15803d; background: #dcfce7; padding: 2px 8px; border-radius: 999px; font-size: 0.78rem; font-weight: 600; }
    .status-rejected { color: #b91c1c; background: #fee2e2; padding: 2px 8px; border-radius: 999px; font-size: 0.78rem; font-weight: 600; }
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
    <div class="card" style="margin-top: 20px;">
      <h3 style="margin-top:0;">Activity History & Photo Evidence</h3>
      <ul id="history" class="history-list"></ul>
    </div>

    <!-- ADMIN REVIEW PANEL -->
    <div class="card" style="margin-top: 20px;">
      <div style="display:flex; justify-content:space-between; align-items:center; gap:10px; flex-wrap:wrap;">
        <h3 style="margin:0;">🛡️ Admin Evidence Review</h3>
        <button id="toggle-admin-btn" class="secondary small-btn" onclick="toggleAdminPanel()">Unlock Admin (PIN: 1234)</button>
      </div>

      <div id="admin-panel" class="hidden" style="margin-top:14px;">
        <p style="font-size:0.85rem; color:#64748b; margin-top:0;">I-approve ang valid na picture ng basura para ma-credit ang points sa user.</p>
        <ul id="admin-queue" class="history-list"></ul>
      </div>
    </div>
  </div>

  <script>
    const PESO_PER_POINT = 0.10;
    const ADMIN_PIN = "1234";

    let isSignUp = false;
    let isAdminUnlocked = false;
    let users = JSON.parse(localStorage.getItem("ecoUsers")) || {};
    let currentEmail = localStorage.getItem("ecoCurrentUser") || null;
    let currentCompressedPhoto = null;

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

      if (!email || !password) return (authError.textContent = "Ilagay ang email at password.");

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
      isAdminUnlocked = false;
      document.getElementById("admin-panel").classList.add("hidden");
      document.getElementById("toggle-admin-btn").textContent = "Unlock Admin (PIN: 1234)";
      localStorage.removeItem("ecoCurrentUser");
      authScreen.classList.remove("hidden");
      appScreen.classList.add("hidden");
    };

    window.previewPhoto = (event) => {
      const file = event.target.files[0];
      if (!file) return;

      const reader = new FileReader();
      reader.onload = (e) => {
        const img = new Image();
        img.onload = () => {
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
    };

    window.submitTrashWithPhoto = () => {
      const msg = document.getElementById("submit-msg");
      msg.style.color = "#dc2626";

      if (!currentCompressedPhoto) {
        return (msg.textContent = "⚠️ Kailangan muna mag-upload o mag-picture ng basura bago mag-submit!");
      }

      const [actionLabel, ptsStr] = document.getElementById("trash-type").value.split("|");
      const pts = Number(String(ptsStr).replace(/,/g, "")) || 0;
      const user = users[currentEmail];

      const entryId = "ev_" + Date.now() + "_" + Math.random().toString(36).slice(2, 6);
      user.logs.unshift({
        id: entryId,
        type: "evidence",
        status: "pending",
        pts,
        actionLabel,
        date: new Date().toLocaleDateString(),
        text: `${actionLabel} (${pts.toLocaleString()} pts) — ${new Date().toLocaleDateString()}`,
        photo: currentCompressedPhoto
      });

      currentCompressedPhoto = null;
      document.getElementById("trash-photo").value = "";
      document.getElementById("photo-preview").style.display = "none";
      document.getElementById("upload-label").textContent = "📷 I-click para kumuha o pumili ng picture";

      msg.style.color = "#15803d";
      msg.textContent = `Naisumite ang picture! Magkakaroon ng +${pts.toLocaleString()} pts kapag na-approve sa Admin Review.`;
      saveData();
    };

    window.toggleAdminPanel = () => {
      const panel = document.getElementById("admin-panel");
      const btn = document.getElementById("toggle-admin-btn");

      if (!isAdminUnlocked) {
        const pin = prompt("Ilagay ang Admin PIN:");
        if (pin !== ADMIN_PIN) {
          alert("Maling Admin PIN.");
          return;
        }
        isAdminUnlocked = true;
        panel.classList.remove("hidden");
        btn.textContent = "Lock Admin";
        renderAdminQueue();
      } else {
        isAdminUnlocked = false;
        panel.classList.add("hidden");
        btn.textContent = "Unlock Admin (PIN: 1234)";
      }
    };

    window.reviewEvidence = (userEmail, entryId, decision) => {
      const targetUser = users[userEmail];
      if (!targetUser) return;
      const item = targetUser.logs.find(log => log && log.id === entryId);
      if (!item || item.status !== "pending") return;

      if (decision === "approve") {
        item.status = "approved";
        targetUser.points = (Number(targetUser.points) || 0) + (Number(item.pts) || 0);
        item.text = `+${Number(item.pts).toLocaleString()} pts — ${item.actionLabel} (${item.date})`;
      } else {
        item.status = "rejected";
        item.text = `0 pts — ${item.actionLabel} (${item.date}) [Rejected]`;
      }

      saveData();
    };

    function renderAdminQueue() {
      if (!isAdminUnlocked) return;
      const queueEl = document.getElementById("admin-queue");
      const pendingItems = [];

      Object.entries(users).forEach(([email, u]) => {
        (u.logs || []).forEach(item => {
          if (item && item.type === "evidence" && item.status === "pending") {
            pendingItems.push({ email, userName: u.name, item });
          }
        });
      });

      if (!pendingItems.length) {
        queueEl.innerHTML = "<li style='color:#64748b; font-size:0.9rem;'>Walang pending na picture para i-review ngayon.</li>";
        return;
      }

      queueEl.innerHTML = pendingItems.map(({ email, userName, item }) => `
        <li class="history-item">
          <div class="history-left">
            ${item.photo ? `<img src="${item.photo}" class="evidence-thumb" alt="Evidence" />` : ""}
            <div>
              <div><strong>${userName}</strong> (${email})</div>
              <div style="font-size:0.85rem; color:#475569;">${item.text}</div>
            </div>
          </div>
          <div style="display:flex; gap:6px;">
            <button class="small-btn" onclick="reviewEvidence('${email}', '${item.id}', 'approve')">Approve</button>
            <button class="small-btn danger" onclick="reviewEvidence('${email}', '${item.id}', 'reject')">Reject</button>
          </div>
        </li>
      `).join("");
    }

    function getStatusBadge(item) {
      if (!item || item.type !== "evidence") return "";
      if (item.status === "approved") return `<span class="status-approved">Approved</span>`;
      if (item.status === "rejected") return `<span class="status-rejected">Rejected</span>`;
      return `<span class="status-pending">Pending Review</span>`;
    }

    function showDashboard() {
      const user = users[currentEmail];
      if (!user) return;
      const safePoints = Number(user.points) || 0;
      document.getElementById("user-name").textContent = user.name;
      document.getElementById("balance").textContent = safePoints.toLocaleString();
      document.getElementById("peso-balance").textContent = (safePoints * PESO_PER_POINT).toFixed(2);

      const historyEl = document.getElementById("history");
      if (!user.logs.length) {
        historyEl.innerHTML = "<li style='color:#64748b; font-size:0.9rem;'>Wala pang activity. Mag-picture ng basura para mag-ipon ng points!</li>";
      } else {
        historyEl.innerHTML = user.logs.map(item => {
          if (typeof item === "string") {
            return `<li class="history-item"><div class="history-left"><span>${item}</span></div></li>`;
          }
          return `
            <li class="history-item">
              <div class="history-left">
                ${item.photo ? `<img src="${item.photo}" class="evidence-thumb" alt="Evidence" />` : ""}
                <span>${item.text}</span>
              </div>
              ${getStatusBadge(item)}
            </li>
          `;
        }).join("");
      }

      renderAdminQueue();
      authScreen.classList.add("hidden");
      appScreen.classList.remove("hidden");
    }

    function saveData() {
      localStorage.setItem("ecoUsers", JSON.stringify(users));
      showDashboard();
    }

    window.requestGCashCashout = () => {
      const user = users[currentEmail];
      const safePoints = Number(user.points) || 0;
      const ptsRequired = Number(document.getElementById("cashout-tier").value);
      const pesoAmount = ptsRequired * PESO_PER_POINT;
      const gcashNumber = document.getElementById("gcash-number").value.trim();
      const gcashName = document.getElementById("gcash-name").value.trim();
      const msg = document.getElementById("cashout-msg");

      msg.style.color = "#dc2626";
      if (safePoints < ptsRequired) return (msg.textContent = `Kulang pa ang points mo. Kailangan ng ${ptsRequired.toLocaleString()} pts.`);
      if (!/^09\d{9}$/.test(gcashNumber)) return (msg.textContent = "Ilagay ang tamang 11-digit GCash number (09xxxxxxxxx).");
      if (!gcashName) return (msg.textContent = "Ilagay ang pangalan ng GCash account.");

      user.points = safePoints - ptsRequired;
      user.logs.unshift({
        type: "cashout",
        text: `-${ptsRequired.toLocaleString()} pts — GCash Cashout ₱${pesoAmount.toFixed(2)} to ${gcashNumber} (${gcashName}) [Pending]`,
        photo: null
      });
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
