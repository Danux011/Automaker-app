<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Layland Bus Accurate Calculator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f1f5f9;
      padding: 20px;
      max-width: 700px;
      margin: auto;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
      color: #0f172a;
    }
    label, input, .output {
      display: block;
      width: 100%;
      margin-bottom: 15px;
      font-size: 1rem;
    }
    input[type="number"] {
      padding: 10px;
      border-radius: 6px;
      border: 1px solid #ccc;
    }
    button {
      background: #2563eb;
      color: white;
      border: none;
      padding: 10px;
      font-size: 1rem;
      cursor: pointer;
      border-radius: 8px;
    }
    button:hover {
      background: #1e40af;
    }
    .output {
      background: #ffffff;
      padding: 15px;
      border: 1px solid #ccc;
      border-radius: 10px;
    }
    .output p {
      margin: 6px 0;
    }
  </style>
</head>
<body>
  <h2>Layland Bus Accurate Model Calculator</h2><label for="length">Enter Desired Bus Length (cm):</label> <input type="number" id="length" placeholder="e.g. 60" min="10" max="200">

<button onclick="calculate()">Calculate Dimensions</button>

  <div class="output" id="resultBox" style="display: none;"></div>  <script>
    function calculate() {
      const length = parseFloat(document.getElementById("length").value);
      const resultBox = document.getElementById("resultBox");

      if (isNaN(length) || length < 10 || length > 200) {
        resultBox.innerHTML = "Please enter a valid length between 10 and 200 cm.";
        resultBox.style.display = "block";
        return;
      }

      // Ratios from 60cm standard:
      const width = (length * 17 / 60).toFixed(1);
      const height = (length * 20 / 60).toFixed(1);

      const lowerPanelHeight = (length * 10 / 60).toFixed(1);
      const mainWindowW = (length * 9.2 / 60).toFixed(1);
      const mainWindowH = (length * 6.2 / 60).toFixed(1);
      const smallWindowW = (length * 5.8 / 60).toFixed(1);
      const smallWindowH = (length * 6.2 / 60).toFixed(1);
      const frontGlassW = (length * 7.2 / 60).toFixed(1);
      const frontGlassH = (length * 6.3 / 60).toFixed(1);
      const rearGlassW = (length * 15 / 60).toFixed(1);
      const rearGlassH = (length * 6 / 60).toFixed(1);
      const wheelArchW = (length * 8.5 / 60).toFixed(1);
      const wheelArchH = (length * 5 / 60).toFixed(1);
      const doorWidth = (length * 5 / 60).toFixed(1);

      resultBox.innerHTML = `
        <p>🚌 <strong>Main Dimensions:</strong></p>
        <p>🔸 Length: ${length} cm</p>
        <p>🔸 Width: ${width} cm</p>
        <p>🔸 Height: ${height} cm</p>

        <p>🧱 <strong>Body Detail Dimensions:</strong></p>
        <p>🔹 Lower Body Panel Height: ${lowerPanelHeight} cm</p>
        <p>🔹 Main Window (W × H): ${mainWindowW} × ${mainWindowH} cm</p>
        <p>🔹 Small Window (W × H): ${smallWindowW} × ${smallWindowH} cm</p>
        <p>🔹 Front Glass (W × H): ${frontGlassW} × ${frontGlassH} cm</p>
        <p>🔹 Rear Glass (W × H): ${rearGlassW} × ${rearGlassH} cm</p>
        <p>🔹 Wheel Arch (W × H): ${wheelArchW} × ${wheelArchH} cm</p>
        <p>🔹 Door Width: ${doorWidth} cm</p>
      `;
      resultBox.style.display = "block";
    }
  </script></body>
</html>
