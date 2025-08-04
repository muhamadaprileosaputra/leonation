<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>LEONATION Rank</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
      background: #ffffff;
      color: #000000;
    }

    .container {
      width: 90%;
      max-width: 700px;
      margin: 40px auto;
      padding: 30px;
      background-color: rgba(0, 0, 0, 0.8);
      border-radius: 15px;
      box-sizing: border-box;
      color: white;
    }

    h1 {
      font-size: 2.8em;
      color: #00bfff;
      text-align: center;
      margin-bottom: 40px;
    }

    h2 {
      text-align: center;
      margin-bottom: 20px;
    }

    ul {
      list-style: none;
      padding: 0;
      margin-bottom: 30px;
    }

    li {
      padding: 8px 0;
      border-bottom: 1px solid #444;
    }

    label {
      display: block;
      margin-top: 20px;
      font-weight: bold;
    }

    input, select {
      width: 100%;
      padding: 12px;
      margin-top: 10px;
      border-radius: 8px;
      border: none;
      font-size: 1em;
      background-color: white;
      color: black;
      box-sizing: border-box;
    }

    .wa-button {
      display: block;
      width: 100%;
      margin-top: 30px;
      padding: 16px 0;
      font-size: 17px;
      font-weight: bold;
      color: white;
      background-color: #25D366;
      border: none;
      border-radius: 10px;
      text-align: center;
      text-decoration: none;
      transition: background 0.3s ease;
    }

    .wa-button:hover {
      background-color: #1ebe5d;
    }

    #totalPrice {
      margin-top: 20px;
      font-weight: bold;
      color: #00ff99;
      font-size: 18px;
    }

    @media (min-width: 768px) {
      .container {
        max-width: 750px;
        padding: 40px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>LEONATION</h1>

    <h2>HARGA RANK SERVER</h2>
    <ul>
      <li>SUPPORTER = 5.000 IDR</li>
      <li>VIP = 10.000 IDR</li>
      <li>MVP = 20.000 IDR</li>
      <li>ELITE = 30.000 IDR</li>
      <li>MASTER = 40.000 IDR</li>
      <li>LEGENDS = 50.000 IDR</li>
      <li>MYTHIC = 60.000 IDR</li>
      <li>ULTRA = 70.000 IDR</li>
      <li>VENOM = 80.000 IDR</li>
      <li>IMMORTAL = 90.000 IDR</li>
      <li>MICHAEL = 100.000 IDR</li>
    </ul>

    <p style="text-align: center; font-weight: bold; color: #00ff99;">FITUR RANK TANYA DENGAN ADMIN</p>
    <p style="text-align: center;"><strong>RANK BAYAR PERBULAN / 30 HARI 1×</strong></p>

    <label for="playerName">Nama Player Minecraft:</label>
    <input type="text" id="playerName" placeholder="Contoh: Steve_MC123" />

    <label for="rank">Pilih Rank:</label>
    <select id="rank" onchange="updateTotal()">
      <option value="SUPPORTER">SUPPORTER - 5.000 IDR</option>
      <option value="VIP">VIP - 10.000 IDR</option>
      <option value="MVP">MVP - 20.000 IDR</option>
      <option value="ELITE">ELITE - 30.000 IDR</option>
      <option value="MASTER">MASTER - 40.000 IDR</option>
      <option value="LEGENDS">LEGENDS - 50.000 IDR</option>
      <option value="MYTHIC">MYTHIC - 60.000 IDR</option>
      <option value="ULTRA">ULTRA - 70.000 IDR</option>
      <option value="VENOM">VENOM - 80.000 IDR</option>
      <option value="IMMORTAL">IMMORTAL - 90.000 IDR</option>
      <option value="MICHAEL">MICHAEL - 100.000 IDR</option>
    </select>

    <label for="duration">Pilih Masa Aktif Rank:</label>
    <select id="duration" onchange="updateTotal()">
      <option value="1">1 BULAN / 30 HARI</option>
      <option value="2">2 BULAN / 60 HARI</option>
    </select>

    <p id="totalPrice">Total Harga: 5.000 IDR</p>

    <a class="wa-button" href="#" onclick="sendWA()">Beli via WhatsApp</a>
  </div>

  <script>
    const rankPrices = {
      "SUPPORTER": 5000,
      "VIP": 10000,
      "MVP": 20000,
      "ELITE": 30000,
      "MASTER": 40000,
      "LEGENDS": 50000,
      "MYTHIC": 60000,
      "ULTRA": 70000,
      "VENOM": 80000,
      "IMMORTAL": 90000,
      "MICHAEL": 100000
    };

    function updateTotal() {
      const rank = document.getElementById('rank').value;
      const duration = parseInt(document.getElementById('duration').value);
      const total = rankPrices[rank] * duration;

      document.getElementById('totalPrice').innerText = `Total Harga: ${total.toLocaleString()} IDR`;
    }

    function sendWA() {
      const name = document.getElementById('playerName').value.trim();
      const rank = document.getElementById('rank').value;
      const duration = parseInt(document.getElementById('duration').value);
      const total = rankPrices[rank] * duration;

      if (!name) {
        alert("Masukkan nama player dulu ya.");
        return;
      }

      const durasiText = duration === 1 ? "1 BULAN / 30 HARI" : "2 BULAN / 60 HARI";
      const message = `Halo Admin, saya ingin membeli rank:\n\nRank: ${rank}\nMasa Aktif Rank : ${durasiText}\nNama Player: ${name}\nTotal Harga: ${total.toLocaleString()} IDR`;
      const encoded = encodeURIComponent(message);
      const phone = "6285189826843";

      window.open(`https://wa.me/${phone}?text=${encoded}`, "_blank");
    }

    // Set total awal saat load
    window.onload = updateTotal;
  </script>
</body>
</html>
