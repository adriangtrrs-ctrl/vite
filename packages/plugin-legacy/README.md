<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Quortex Analyzer</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #f0f2f5;
      text-align: center;
    }
    .container {
      background: #fff;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      max-width: 600px;
      margin: 0 auto;
    }
    input[type="file"] {
      margin: 20px 0;
    }
    canvas {
      margin-top: 20px;
      max-width: 100%;
    }
    .result {
      margin-top: 20px;
      font-size: 1.2em;
      color: #333;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Quortex Analyzer</h1>
    <p>Envie um print da análise da Quortex:</p>
    <input type="file" id="upload" accept="image/*" />
    <canvas id="canvas"></canvas>
    <div class="result" id="result">Nenhuma análise realizada ainda.</div>
  </div>

  <script>
    const upload = document.getElementById("upload");
    const canvas = document.getElementById("canvas");
    const ctx = canvas.getContext("2d");
    const result = document.getElementById("result");

    upload.addEventListener("change", (event) => {
      const file = event.target.files[0];
      if (!file) return;

      const reader = new FileReader();
      reader.onload = function (e) {
        const img = new Image();
        img.onload = function () {
          canvas.width = img.width;
          canvas.height = img.height;
          ctx.drawImage(img, 0, 0);
          analyzeImage();
        };
        img.src = e.target.result;
      };
      reader.readAsDataURL(file);
    });

    function analyzeImage() {
      // Simulação de análise simples (IA real entraria aqui futuramente)
      // Aqui você poderia usar visão computacional real com uma API externa
      const simulatedPatterns = [
        "Tendência de alta detectada",
        "Reversão próxima identificada",
        "Zona de consolidação aparente",
        "Entrada possível nas próximas odds",
        "Risco elevado — aguarde confirmação"
      ];
      const randomResult = simulatedPatterns[Math.floor(Math.random() * simulatedPatterns.length)];
      result.textContent = `🔍 ${randomResult}`;
    }
  </script>
</body>
</html>
