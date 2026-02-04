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
      background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
      display: flex;
      align-items: center;
      justify-content: center;
      color: #fff;
    }

    .card {
      background: rgba(255, 255, 255, 0.08);
      backdrop-filter: blur(10px);
      border-radius: 20px;
      padding: 40px 32px;
      max-width: 420px;
      width: 90%;
      text-align: center;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4);
      animation: fadeIn 1.2s ease;
    }

    h1 {
      font-size: 1.8rem;
      margin-bottom: 12px;
      font-weight: 600;
    }

    p {
      font-size: 1rem;
      line-height: 1.6;
      opacity: 0.9;
      margin-bottom: 28px;
    }

    button {
      background: #ffffff;
      color: #203a43;
      border: none;
      border-radius: 999px;
      padding: 14px 28px;
      font-size: 1rem;
      cursor: pointer;
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(255, 255, 255, 0.25);
    }

    .hidden {
      display: none;
    }

    .heart {
      font-size: 2.5rem;
      animation: pulse 1.5s infinite;
      margin-bottom: 16px;
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
  <div class="card" id="step1">
    <h1>Hey you.</h1>
    <p>
      I know we’re not in the same place right now,
      but you’ve still been the person on my mind every day.
    </p>
    <button onclick="nextStep()">Continue</button>
  </div>

  <div class="card hidden" id="step2">
    <p>
      I wanted to do something instead of just saying something.
      Something you could open and feel.
    </p>
    <button onclick="finalStep()">One more thing</button>
  </div>

  <div class="card hidden" id="step3">
    <div class="heart">❤️</div>
    <h1>Be my Valentine?</h1>
    <p>
      Not just for the day.
      But because it’s you.
    </p>
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
