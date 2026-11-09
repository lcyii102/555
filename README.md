
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>今晚想追甚麼樣的劇？</title>

<style>
  body {
    font-family: sans-serif;
    background: #f5f0ff;
    text-align: center;
    padding: 30px 15px;
  }

  .container {
    max-width: 450px;
    margin: auto;
    background: white;
    padding: 25px;
    border-radius: 18px;
    box-shadow: 0 4px 15px #0001;
  }

  h1 {
    color: #9333ea;
  }

  textarea {
    width: 100%;
    box-sizing: border-box;
    height: 170px;
    padding: 12px;
    font-size: 17px;
    border: 1px solid #ddd;
    border-radius: 10px;
    resize: vertical;
  }

  button {
    width: 100%;
    margin-top: 18px;
    padding: 15px;
    background: #9333ea;
    color: white;
    border: none;
    border-radius: 10px;
    font-size: 20px;
    cursor: pointer;
  }

  button:hover {
    background: #7e22ce;
  }

  #result {
    margin-top: 25px;
    padding: 20px;
    background: #f3e8ff;
    border-radius: 12px;
    font-size: 24px;
    font-weight: bold;
    color: #6b21a8;
  }
</style>
</head>

<body>

<div class="container">

  <h1>📺 今晚想追甚麼樣的劇？</h1>

  <p>輸入想看的劇情類型，每行一個選項</p>

  <textarea id="options">懸疑推理
療癒日常
經典老片
驚悚恐怖
動作打鬥</textarea>

  <button onclick="draw()">🎲 幫我選！</button>

  <div id="result">
    等待抽籤結果...
  </div>

</div>

<script>

function draw() {

  // 讀取文字輸入區
  const input = document.getElementById("options").value;

  // 去除前後空白及空白行
  const cleaned = input
    .split("\n")
    .map(item => item.trim())
    .filter(item => item !== "");

  // 去除完全相同的重複選項
  const options = [...new Set(cleaned)];

  const result = document.getElementById("result");

  // 檢查清單是否為空
  if (options.length === 0) {
    result.textContent = "請先輸入至少一個選項";
    return;
  }

  // 每個有效選項有相同的中籤機率
  const index = Math.floor(Math.random() * options.length);

  // 顯示抽籤結果
  result.textContent = "🎉 今晚就看：" + options[index];

}

</script>

</body>
</html>
