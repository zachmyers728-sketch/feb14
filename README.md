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
      width: 20px;
      height: 20px;
      background: rgba(255, 255, 255, 0.35);
      transform: rotate(45deg);
      animation: float 10s infinite ease-in;
    }

    .heart-bg::before,
    .heart-bg::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background: rgba(255, 255, 255, 0.35);
      border-radius: 50%;
    }

    .heart-bg::before {
      top: -10px;
      left: 0;
    }

    .heart-bg::after {
      left: -10px;
      top: 0;
    }

    @keyframes float {
      0% { transform: translateY(100vh) rotate(45deg); opacity: 0; }
      20% { opacity: 0.6; }
      100% { transform: translateY(-10vh) rotate(45deg); opacity: 0; }
    }

    .card {
      position: relative;
      z-index: 2;
      background: rgba(255, 255, 255, 0.2);
      backdrop-filter: blur(12px);
      border-radius: 24px;
      padding: 42px 34px;
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
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(255, 255, 255, 0.35);
    }

    .hidden { display: none; }

    .big-heart {
      font-size: 2.8rem;
      animation: pulse 1.5s infinite;
      margin-bottom: 16px;
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
  </style>
</head>
<body>

  <!-- background hearts -->
  <div class="heart-bg" style="left:10%; animation-delay:0s"></div>
  <div class="heart-bg" style="left:30%; animation-delay:2s"></div>
  <div class="heart-bg" style="left:50%; animation-delay:4s"></div>
  <div class="heart-bg" style="left:70%; animation-delay:1s"></div>
  <div class="heart-bg" style="left:85%; animation-delay:3s"></div>

  <div class="card" id="step1">
    <h1>Hi pookie!!</h1>
    <p>
      Being far from you everyday is a huge challenge,
      but you really make it worth it
    </p>
    <button onclick="nextStep()">Continue</button>
  </div>

  <div class="card hidden" id="step2">
    <p>
      I love you so much and I cant wait to come visit you
    </p>
    <button onclick="finalStep()">One more thing</button>
  </div>

  <div class="card hidden" id="step3">
    <div class="big-heart">💗</div>
    <h1>Will you be my Valentine?</h1>
    <div class="date">I'm so glad i get to come see you,
    whether your studying or we're out watching monster trucks
    I'll be there soon!</div>
  </div>

  <script>
    function nextStep() {
      document.getElementById('step1').classList.add('hidden');
      document.getElementById('step2').classList.remove('hidden');
    }

    function finalStep() {
      document.getElementById('step2').classList.add('hidden');
      document.getElementById('step3').classList.remove('hidden');
    }
  </script>
</body>
</html>
