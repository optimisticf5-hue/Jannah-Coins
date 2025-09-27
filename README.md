<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#2e7d32">
  <title>Jannah Coins – Kindness is Currency</title>
  <link rel="manifest" href="manifest.json">
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e8f5e9;
      color: #2e7d32;
      text-align: center;
      padding: 2rem;
    }
    h1 {
      font-size: 2rem;
    }
    button {
      background-color: #2e7d32;
      color: #fff;
      border: none;
      padding: 1rem 2rem;
      font-size: 1rem;
      border-radius: 8px;
      margin-top: 1rem;
    }
    .coin {
      position: absolute;
      font-size: 24px;
      color: #2e7d32;
      pointer-events: none;
      animation: flyCoin 1s ease-out forwards;
    }
    @keyframes flyCoin {
      0% { opacity: 1; transform: translateY(0); }
      100% { opacity: 0; transform: translateY(-80px) scale(1.2); }
    }
  </style>
</head>
<body>
  <h1>💚 Jannah Coins 💚</h1>
  <p>Kindness is Currency. Earn coins for good deeds.</p>
  <div id="coins">You have 0 coins</div>
  <div id="msg"></div>
  <button onclick="earnCoin(event)">I did a kind deed</button>

  <script>
    let coins = parseInt(localStorage.getItem('jannahCoins')) || 0;
    const coinsDiv = document.getElementById('coins');
    const msgDiv = document.getElementById('msg');
    coinsDiv.textContent = "You have " + coins + " coins";

    function earnCoin(event) {
      coins++;
      localStorage.setItem('jannahCoins', coins);
      coinsDiv.textContent = "You have " + coins + " coins";

      // Show temporary message
      msgDiv.textContent = "🌟 You did a good deed!";
      setTimeout(() => { msgDiv.textContent = ""; }, 2000);

      // Create flying coin
      const coin = document.createElement('div');
      coin.className = 'coin';
      coin.textContent = '💚';
      document.body.appendChild(coin);

      // Position coin above button
      const rect = event.target.getBoundingClientRect();
      coin.style.left = rect.left + rect.width/2 - 12 + 'px';
      coin.style.top = rect.top - 12 + 'px';

      setTimeout(() => { coin.remove(); }, 1000);
    }

    // Register service worker for offline capability
    if ('serviceWorker' in navigator) {
      navigator.serviceWorker.register('sw.js');
    }
  </script>
</body>
</html>
