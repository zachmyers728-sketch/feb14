<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For You</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: "Helvetica Neue", Arial, sans-serif;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      color: #fff;
    }

    /* floating hearts */
    .heart-bg {
      position: absolute;
      width: 18px;
      height: 18px;
      background: rgba(255, 255, 255, 0.4);
      transform: rotate(45deg);
      animation: float 12s infinite ease-in;
    }

    .heart-bg::before,
    .heart-bg::after {
      content: "";
      position: absolute;
      width: 18px;
      height: 18px;
      background: rgba(255, 255, 255, 0.4);
      border-radius: 50%;
    }

    .heart-bg::before { top: -9px; left: 0; }
    .heart-bg::after { left: -9px; top: 0; }

    @keyframes float {
      0% { transform: translateY(100vh) rotate(45deg); opacity: 0; }
      20% { opacity: 0.7; }
      100% { transform: translateY(-10vh) rotate(45deg); opacity: 0; }
    }

    .card {
      position: relative;
      z-index: 2;
      background: rgba(255, 255, 255, 0.22);
      backdrop-filter: blur(14px);
      border-radius: 26px;
      padding: 44px 36px;
      max-width: 420px;
      width: 90%;
      text-align: center;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.25);
      animation: fadeIn 1.2s ease;
    }

    h1 {
      font-size: 1.9rem;
      margin-bottom: 14px;
      font-weight: 600;
    }

    p {
      font-size: 1rem;
      line-height: 1.6;
      opacity: 0.95;
      margin-bottom: 30px;
    }

    button {
      background: #ffffff;
      color: #ff6f91;
      border: none;
      border-radius: 999px;
      padding: 14px 30px;
      font-size: 1rem;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
      margin: 6px;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(255, 255, 255, 0.35);
    }

    .hidden { display: none; }

    .big-heart {
      font-size: 3rem;
      animation: pulse 1.5s infinite;
      margin-bottom: 18px;
    }

    .date {
      margin-top: 18px;
      font-size: 0.9rem;
      letter-spacing: 1px;
      opacity: 0.9;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.15); }
      100% { transform: scale(1); }
    }

    .confetti {
      position: fixed;
      top: -10px;
      font-size: 1.2rem;
      animation: fall 3s linear forwards;
      z-index: 5;
    }

    @keyframes fall {
      to { transform: translateY(110vh) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>

  <!-- background hearts -->
  <div class="heart-bg" style="left:10%; animation-delay:0s"></div>
  <div class="heart-bg" style="left:25%; animation-delay:3s"></div>
  <div class="heart-bg" style="left:45%; animation-delay:1s"></div>
  <div class="heart-bg" style="left:65%; animation-delay:4s"></div>
  <div class="heart-bg" style="left:80%; animation-delay:2s"></div>

  <!-- Step 1 -->
  <div class="card" id="step1">
    <h1 id="nameLine">Hi pookie!!</h1>
    <p>
      Being far from you everyday is such a challenge,
      but you really make it worth it
    </p>
    <button onclick="nextStep()">Continue</button>
  </div>

  <!-- Step 2 -->
  <div class="card hidden" id="step2">
    <p>
      I love you so much,
      and I can't wait to come visit you
    </p>
    <button onclick="finalStep()">One more thing</button>
  </div>

  <!-- Step 3 -->
  <div class="card hidden" id="step3">
    <div class="big-heart">💗</div>
    <h1>Will you be my Valentine?</h1>
    <div>
      <button onclick="sayYes()">Yes</button>
    </div>
    <div class="date">I'm so glad I get to come see you,
    whether your studying or we're out watching monster trucks,
    I'll be there soon!</div>
  </div>

  <!-- Step 4 -->
  <div class="card hidden" id="step4">
    <div class="big-heart">💖</div>
    <h1>:)</h1>
    <p>I can’t wait to see you.</p>
  </div>

  <!-- music (starts only after interaction) -->
  <audio id="music" loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/10/25/audio_8b0b4f4c7b.mp3" type="audio/mpeg">
  </audio>

  <script>
    // name from URL ?name=
    const params = new URLSearchParams(window.location.search);
    const name = params.get('name');
    if (name) {
      document.getElementById('nameLine').textContent = `Hey ${name}.`;
    }

    function nextStep() {
      document.getElementById('step1').classList.add('hidden');
      document.getElementById('step2').classList.remove('hidden');
    }

    function finalStep() {
      document.getElementById('step2').classList.add('hidden');
      document.getElementById('step3').classList.remove('hidden');
    }

    function sayYes() {
      document.getElementById('step3').classList.add('hidden');
      document.getElementById('step4').classList.remove('hidden');
      playMusic();
      confetti();
    }

    function playMusic() {
      const music = document.getElementById('music');
      music.volume = 0.5;
      music.play();
    }

    function confetti() {
      for (let i = 0; i < 30; i++) {
        const el = document.createElement('div');
        el.className = 'confetti';
        el.textContent = ['💗','💖','💕','💞'][Math.floor(Math.random() * 4)];
        el.style.left = Math.random() * 100 + 'vw';
        el.style.animationDelay = Math.random() * 0.5 + 's';
        document.body.appendChild(el);
        setTimeout(() => el.remove(), 3000);
      }
    }
  </script>
</body>
</html>
