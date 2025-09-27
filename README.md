<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🌿 Jannah Coins</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e8f5e9;
      text-align: center;
      padding: 50px;
    }
    h1 {
      color: #2e7d32;
      font-size: 2.5em;
      margin-bottom: 10px;
    }
    p.subtitle {
      color: #1b5e20;
      font-size: 1.2em;
      margin-bottom: 30px;
    }
    button {
      background: #2e7d32;
      color: white;
      border: none;
      padding: 15px 30px;
      font-size: 18px;
      border-radius: 12px;
      cursor: pointer;
      transition: background 0.3s;
    }
    button:hover {
      background: #1b5e20;
    }
    #coins {
      font-size: 22px;
      color: #1b5e20;
      margin-top: 25px;
    }
  </style>
</head>
<body>
  <h1>🌿 Jannah Coins</h1>
  <p class="subtitle">Kindness is currency</p>
  <button onclick="earnCoin()">Earn 1 Jannah Coin</button>
  <div id="coins">You have 0 coins</div>

  <script>
    // Load saved coins or start at 0
    let coins = parseInt(localStorage.getItem('jannahCoins')) || 0;
    const coinsDiv = document.getElementById('coins');
    coinsDiv.textContent = "You have " + coins + " coins";

    // Function to earn a coin
    function earnCoin() {
      coins++;
      localStorage.setItem('jannahCoins', coins);
      coinsDiv.textContent = "You have " + coins + " coins";
    }
  </script>
</body>
</html>
