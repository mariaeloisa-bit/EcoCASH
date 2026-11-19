<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EcoPoints — Sustainability Rewards</title>
  <style>
    :root { --primary: #1b7a43; --bg: #f3f8f4; --card: #ffffff; --text: #1e293b; }
    body { font-family: system-ui, sans-serif; background: var(--bg); color: var(--text); margin: 0; padding: 20px; }
    .container { max-width: 720px; margin: 0 auto; }
    header { background: var(--primary); color: white; padding: 24px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; }
    .points-badge { font-size: 2rem; font-weight: bold; background: rgba(255,255,255,0.2); padding: 8px 16px; border-radius: 8px; }
    .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 20px; }
    .card { background: var(--card); padding: 20px; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.06); }
    button { background: var(--primary); color: white; border: none; padding: 10px 14px; border-radius: 6px; cursor: pointer; font-weight: 600; width: 100%; margin-top: 8px; }
    button:hover { opacity: 0.9; }
    button.redeem { background: #0f766e; }
    ul { padding-left: 20px; font-size: 0.9rem; color: #475569; }
    @media (max-width: 600px) { .grid { grid-template-columns: 1fr; } }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div>
        <h1 style="margin:0;">🌱 EcoPoints</h1>
        <p style="margin:4px 0 0; opacity:0.9;">Track green habits. Redeem real rewards.</p>
      </div>
      <div class="points-badge"><span id="balance">0</span> pts</div>
    </header>

    <div class="grid">
      <div class="card">
        <h3>Log an Eco-Action</h3>
        <button onclick="earnPoints('Recycled plastics/cans', 20)">♻️ Recycle Waste (+20 pts)</button>
        <button onclick="earnPoints('Used reusable tumbler/bag', 15)">🥤 Bring Reusable Tumbler (+15 pts)</button>
        <button onclick="earnPoints('Commuted by bike/walk', 30)">🚲 Walk or Bike Commute (+30 pts)</button>
        <button onclick="earnPoints('Planted a tree/seedling', 100)">🌳 Plant a Seedling (+100 pts)</button>
      </div>

      <div class="card">
        <h3>Rewards Store</h3>
        <button class="redeem" onclick="redeemReward('₱50 Coffee Voucher', 100)">☕ ₱50 Coffee Voucher (100 pts)</button>
        <button class="redeem" onclick="redeemReward('Bamboo Utensil Set', 250)">🥢 Bamboo Utensil Set (250 pts)</button>
        <button class="redeem" onclick="redeemReward('Plant 1 Real Tree Donation', 500)">🌲 Fund 1 Tree Planting (500 pts)</button>
      </div>
    </div>

    <div class="card" style="margin-top: 20px;">
      <h3>Activity History</h3>
      <ul id="history"></ul>
    </div>
  </div>

  <script>
    let points = Number(localStorage.getItem('ecoPoints')) || 0;
    let logs = JSON.parse(localStorage.getItem('ecoLogs')) || [];

    function updateUI() {
      document.getElementById('balance').textContent = points;
      const list = document.getElementById('history');
      list.innerHTML = logs.map(item => `<li>${item}</li>`).join('') || '<li>No activity yet. Start logging above!</li>';
      localStorage.setItem('ecoPoints', points);
      localStorage.setItem('ecoLogs', JSON.stringify(logs));
    }

    function earnPoints(action, amount) {
      points += amount;
      logs.unshift(`+${amount} pts — ${action} (${new Date().toLocaleTimeString()})`);
      updateUI();
    }

    function redeemReward(reward, cost) {
      if (points < cost) return alert('Not enough EcoPoints yet!');
      points -= cost;
      logs.unshift(`-${cost} pts — Redeemed: ${reward}`);
      updateUI();
    }

    updateUI();
  </script>
</body>
</html>
