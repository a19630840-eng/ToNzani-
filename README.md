<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>A little something for you 🌸</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;1,400&family=Lato:wght@300;400&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      min-height: 100vh;
      background: linear-gradient(135deg, #ffe4ec 0%, #ffc2d4 40%, #ffb3c6 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Lato', sans-serif;
      padding: 24px;
      overflow-x: hidden;
    }

    /* floating petals */
    .petal {
      position: fixed;
      font-size: 1.3rem;
      opacity: 0.45;
      animation: fall linear infinite;
      pointer-events: none;
      user-select: none;
    }
    @keyframes fall {
      0%   { transform: translateY(-60px) rotate(0deg); opacity: 0.5; }
      100% { transform: translateY(110vh) rotate(360deg); opacity: 0; }
    }

    .card {
      background: rgba(255, 255, 255, 0.62);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1.5px solid rgba(255,182,203,0.55);
      border-radius: 28px;
      padding: 48px 44px 44px;
      max-width: 480px;
      width: 100%;
      text-align: center;
      box-shadow: 0 8px 40px rgba(255,105,135,0.13), 0 2px 10px rgba(255,105,135,0.08);
      position: relative;
      z-index: 1;
    }

    .crown {
      font-size: 2.2rem;
      margin-bottom: 6px;
      display: block;
      animation: bob 3s ease-in-out infinite;
    }
    @keyframes bob { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-6px)} }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 1.75rem;
      font-weight: 600;
      color: #c2185b;
      margin-bottom: 4px;
      letter-spacing: 0.01em;
    }

    .subtitle {
      font-size: 0.82rem;
      color: #e57397;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      margin-bottom: 28px;
    }

    /* poem */
    .poem {
      background: linear-gradient(135deg, #fff0f5, #ffe4ec);
      border-left: 3px solid #f06292;
      border-radius: 12px;
      padding: 18px 20px;
      margin-bottom: 28px;
      text-align: left;
    }
    .poem-label {
      font-size: 0.7rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: #f06292;
      margin-bottom: 10px;
      font-weight: 400;
    }
    .poem p {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 0.98rem;
      color: #ad1457;
      line-height: 1.85;
    }

    /* message */
    .message {
      font-size: 0.97rem;
      color: #6d2b45;
      line-height: 1.75;
      margin-bottom: 30px;
      font-weight: 300;
    }
    .message .highlight {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      color: #c2185b;
      font-size: 1.05rem;
    }

    /* input */
    .input-wrap {
      position: relative;
      margin-bottom: 18px;
    }
    .input-wrap input {
      width: 100%;
      padding: 14px 18px 14px 44px;
      border: 1.5px solid #f48fb1;
      border-radius: 50px;
      font-size: 1rem;
      font-family: 'Lato', sans-serif;
      color: #880e4f;
      background: rgba(255,255,255,0.8);
      outline: none;
      transition: border-color 0.25s, box-shadow 0.25s;
      letter-spacing: 0.05em;
    }
    .input-wrap input::placeholder { color: #f48fb1; }
    .input-wrap input:focus {
      border-color: #e91e8c;
      box-shadow: 0 0 0 3px rgba(233,30,140,0.12);
    }
    .input-icon {
      position: absolute;
      left: 16px;
      top: 50%;
      transform: translateY(-50%);
      font-size: 1.1rem;
      pointer-events: none;
    }

    button {
      width: 100%;
      padding: 14px;
      background: linear-gradient(135deg, #f06292, #e91e8c);
      color: #fff;
      border: none;
      border-radius: 50px;
      font-size: 1rem;
      font-family: 'Lato', sans-serif;
      font-weight: 400;
      letter-spacing: 0.06em;
      cursor: pointer;
      transition: transform 0.18s, box-shadow 0.18s;
      box-shadow: 0 4px 18px rgba(233,30,140,0.28);
    }
    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 22px rgba(233,30,140,0.38);
    }
    button:active { transform: translateY(0); }

    /* success */
    .success {
      display: none;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }
    .success-emoji { font-size: 3rem; animation: pop 0.4s cubic-bezier(.36,1.6,.5,1); }
    @keyframes pop { 0%{transform:scale(0)} 100%{transform:scale(1)} }
    .success h2 {
      font-family: 'Playfair Display', serif;
      color: #c2185b;
      font-size: 1.4rem;
    }
    .success p { color: #ad1457; font-size: 0.9rem; font-weight: 300; }

    .divider {
      height: 1px;
      background: linear-gradient(90deg, transparent, #f48fb1, transparent);
      margin: 22px 0;
    }

    .footer-note {
      font-size: 0.72rem;
      color: #e57397;
      letter-spacing: 0.05em;
    }
  </style>
</head>
<body>

  <!-- floating petals -->
  <script>
    const symbols = ['🌸','🌷','💗','✿','🌺'];
    for (let i = 0; i < 18; i++) {
      const p = document.createElement('span');
      p.className = 'petal';
      p.textContent = symbols[Math.floor(Math.random() * symbols.length)];
      p.style.left = Math.random() * 100 + 'vw';
      p.style.animationDuration = (6 + Math.random() * 8) + 's';
      p.style.animationDelay = (Math.random() * 8) + 's';
      p.style.fontSize = (0.9 + Math.random() * 1) + 'rem';
      document.body.appendChild(p);
    }
  </script>

  <div class="card">
    <span class="crown">🌸</span>
    <h1>For you, darling</h1>
    <p class="subtitle">a little something</p>

    <div class="poem">
      <p class="poem-label">✦ a poem for your hair ✦</p>
      <p>
        Your hair falls long like a quiet evening river,<br>
        dark at its roots where your secrets sleep,<br>
        and at the ends it turns to golden light —<br>
        as if even your strands can't help but glow.
      </p>
    </div>

    <div class="message">
      Okay so — I know it started as a bet, and yes, I won 😌<br><br>
      But between you and me?<br><br>
      <span class="highlight">I genuinely think you're really cute,<br>and I wanted your number way before that bet.</span>
    </div>

    <div class="divider"></div>

    <div id="form-section">
      <p class="message" style="margin-bottom:20px;">
        So… <em>Darling, can I get your number?</em> ❤️
      </p>
      <div class="input-wrap">
        <span class="input-icon">📱</span>
        <input type="tel" id="numberInput" placeholder="your number here..." />
      </div>
      <button onclick="submitNumber()">Send it 🌸</button>
    </div>

    <div class="success" id="success-section">
      <div class="success-emoji">💌</div>
      <h2>Thank you, darling ❤️</h2>
      <p>Your number's been received.<br>Expect a text soon 🌸</p>
    </div>

    <div class="divider"></div>
    <p class="footer-note">made with a little courage & a lot of pink ✨</p>
  </div>

  <script>
    function submitNumber() {
      const input = document.getElementById('numberInput');
      const val = input.value.trim();
      if (!val) {
        input.style.borderColor = '#e91e8c';
        input.placeholder = 'c\'mon, don\'t leave me hanging 🥺';
        setTimeout(() => { input.style.borderColor = '#f48fb1'; input.placeholder = 'your number here...'; }, 2000);
        return;
      }
      document.getElementById('form-section').style.display = 'none';
      const s = document.getElementById('success-section');
      s.style.display = 'flex';
      // store number locally so the creator can retrieve it
      localStorage.setItem('girlNumber', val);
    }
  </script>

</body>
</html>
