# akshitasingh7884-ai.github.io
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Radhe Naam Jaap</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }
    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: radial-gradient(circle at top, #fff7d1, #ff9f43);
      overflow: hidden;
    }.flower {
  position: absolute;
  font-size: 22px;
  animation: float 9s linear infinite;
  opacity: 0.6;
}
@keyframes float {
  0% { transform: translateY(110vh); }
  100% { transform: translateY(-10vh); }
}

.burst {
  position: fixed;
  font-size: 28px;
  animation: burst 1.2s ease-out forwards;
  pointer-events: none;
}
@keyframes burst {
  0% { transform: scale(0); opacity: 1; }
  100% { transform: scale(2.5); opacity: 0; }
}

.card {
  background: rgba(255,255,255,0.95);
  padding: 32px;
  border-radius: 26px;
  width: 360px;
  text-align: center;
  box-shadow: 0 30px 60px rgba(0,0,0,0.25);
  z-index: 2;
}

h1 { font-size: 28px; }
.mantra { font-size: 22px; margin: 12px 0; color: #c0392b; font-weight: 600; }
.count { font-size: 54px; font-weight: 600; color: #8e44ad; margin: 15px 0; }

button {
  width: 100%;
  padding: 14px;
  border: none;
  border-radius: 30px;
  font-size: 17px;
  margin-top: 10px;
  background: linear-gradient(45deg, #ff7a18, #ffb347);
  color: white;
  cursor: pointer;
}

.mala { background: linear-gradient(45deg, #6a11cb, #2575fc); }
.reset { background: linear-gradient(45deg, #c0392b, #e74c3c); }

.history {
  margin-top: 18px;
  background: rgba(0,0,0,0.05);
  border-radius: 14px;
  padding: 10px;
  font-size: 13px;
  max-height: 110px;
  overflow-y: auto;
}

.footer {
  margin-top: 16px;
  font-size: 12px;
  font-weight: 600;
  background: linear-gradient(90deg, #ff6a00, #ee0979);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

  </style>
</head>
<body>  <div class="flower" style="left:10%">🌸</div>
  <div class="flower" style="left:30%">🌼</div>
  <div class="flower" style="left:50%">🌺</div>
  <div class="flower" style="left:70%">🌸</div>
  <div class="flower" style="left:90%">🌼</div>  <div class="card">
    <h1>🌸 Radhe Naam Jaap 🌸</h1>
    <div class="mantra">Radhe Radhe</div>
    <div class="count" id="count">0</div><button onclick="jaap()">Radhe Bolo</button>
<button class="mala" onclick="mala108()">108 Mala Jaap</button>
<button class="reset" onclick="resetCount()">Reset</button>

<div class="history" id="history">📿 Daily Jaap History</div>
<div class="footer">✨ Developed by Sushant Singh ✨</div>

  </div>  <script>
    let count = parseInt(localStorage.getItem('radheCount')) || 0;
    let history = JSON.parse(localStorage.getItem('radheHistory')) || {};
    const countEl = document.getElementById('count');
    const historyEl = document.getElementById('history');

    countEl.innerText = count;

    function today() {
      return new Date().toLocaleDateString();
    }

    function saveHistory(val) {
      const d = today();
      history[d] = (history[d] || 0) + val;
      localStorage.setItem('radheHistory', JSON.stringify(history));
      renderHistory();
    }

    function renderHistory() {
      historyEl.innerHTML = '<b>📿 Daily Jaap History</b><br>';
      for (let d in history) {
        historyEl.innerHTML += `${d} : ${history[d]}<br>`;
      }
    }

    function flowerBurst() {
      for (let i = 0; i < 12; i++) {
        const f = document.createElement('div');
        f.className = 'burst';
        f.innerText = ['🌸','🌼','🌺'][Math.floor(Math.random()*3)];
        f.style.left = Math.random()*100 + 'vw';
        f.style.top = Math.random()*100 + 'vh';
        document.body.appendChild(f);
        setTimeout(()=>f.remove(),1200);
      }
    }

    function jaap() {
      count++;
      countEl.innerText = count;
      localStorage.setItem('radheCount', count);
      saveHistory(1);
      if (count % 108 === 0) flowerBurst();
    }

    function mala108() {
      count += 108;
      countEl.innerText = count;
      localStorage.setItem('radheCount', count);
      saveHistory(108);
      flowerBurst();
    }

    function resetCount() {
      count = 0;
      countEl.innerText = count;
      localStorage.setItem('radheCount', count);
    }

    renderHistory();
  </script></body>
</html>
