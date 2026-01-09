<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>คำนวณค่า BMI</title>
  <style>
    body {
      font-family: Arial, Helvetica, sans-serif;
      background: #f2f6ff;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .card {
      background: #fff;
      padding: 24px 28px;
      border-radius: 16px;
      width: 320px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
      margin-bottom: 16px;
    }
    label {
      display: block;
      margin-top: 12px;
    }
    input {
      width: 100%;
      padding: 8px;
      margin-top: 6px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    button {
      width: 100%;
      margin-top: 16px;
      padding: 10px;
      border: none;
      border-radius: 10px;
      background: #4f7cff;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #3c66e0;
    }
    .result {
      margin-top: 16px;
      text-align: center;
      font-size: 16px;
    }
  </style>
</head>
<body>
  <div class="card">
    <h1>คำนวณค่า BMI</h1>

    <label>น้ำหนัก (กิโลกรัม)</label>
    <input type="number" id="weight" placeholder="เช่น 50" />

    <label>ส่วนสูง (เซนติเมตร)</label>
    <input type="number" id="height" placeholder="เช่น 160" />

    <button onclick="calculateBMI()">คำนวณ</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateBMI() {
      const weight = document.getElementById('weight').value;
      const heightCm = document.getElementById('height').value;
      const resultDiv = document.getElementById('result');

      if (weight === '' || heightCm === '') {
        resultDiv.innerHTML = 'กรุณากรอกข้อมูลให้ครบ';
        return;
      }

      const heightM = heightCm / 100;
      const bmi = weight / (heightM * heightM);
      let status = '';

      if (bmi < 18.5) status = 'ผอม';
      else if (bmi < 25) status = 'ปกติ';
      else if (bmi < 30) status = 'ท้วม';
      else status = 'อ้วน';

      resultDiv.innerHTML = `ค่า BMI ของคุณคือ <b>${bmi.toFixed(2)}</b><br>อยู่ในเกณฑ์: <b>${status}</b>`;
    }
  </script>
</body>
</html>
