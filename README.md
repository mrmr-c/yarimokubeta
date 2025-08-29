
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="マチアプあるある　ヤリモクかどうかを判定する無料診断コンテンツです。ヤリモクチェッカー">
  <meta name="keywords" content="ヤリモク,やりもく,ヤリモクチェッカー,あるある,恋愛,都合の良い女,マチアプ,マッチングアプリ,ヤリモク診断,ヤリモク判定">
  <title>ヤリモク判定くんβ 彡(^)(^)</title>
  <style>
    body {
      font-family: "Hiragino Kaku Gothic ProN", "メイリオ", sans-serif;
      background: #fff8f0;
      color: #333;
      margin: 0;
      padding: 2em 1em;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    h1 {
      color: #d14c4c;
      font-size: 2em;
      margin-bottom: 0.2em;
    }
    .subtitle {
      color: #999;
      font-size: 0.95em;
      margin-bottom: 2em;
      text-align: center;
    }
    .question-block {
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
      padding: 2em;
      max-width: 500px;
      width: 100%;
    }
    .question {
      font-weight: bold;
      margin-bottom: 0.5em;
    }
    .btn-group {
      display: flex;
      gap: 1em;
      margin-bottom: 2em;
    }
    button {
      background: #f3f3f3;
      border: 1px solid #ccc;
      border-radius: 6px;
      padding: 0.5em 1.2em;
      font-size: 1em;
      cursor: pointer;
    }
    button:hover {
      background: #e6e6e6;
    }
    #result {
      margin-top: 2em;
      padding: 1em;
      text-align: center;
      font-weight: bold;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <h1>ヤリモク判定くんβ 彡(^)(^)</h1>
  <div class="subtitle">((( ´w｀ ))) あなたがどう感じたかが、いちばん大切です</div>

  <div class="question-block" id="quiz">
    <div class="question" id="qtext">すぐに『どこに住んでるの？』と聞かれた</div>
    <div class="btn-group">
      <button onclick="answer(true)">はい</button>
      <button onclick="answer(false)">いいえ</button>
    </div>
  </div>

  <div id="result"></div>

  <script>
    const questions = [
      "すぐに『どこに住んでるの？』と聞かれた",
      "すぐ通話しようとしてくる",
      "自分の写真や外見についてしか言及しない",
      "仕事や趣味の話はスルーされがち",
      "“会わないとわからない”などと言う",
      "タメ口で距離がやたら近い",
      "家に来てよ、家行っていい？などの話がすぐ出る",
      "夜遅い時間ばかりに連絡が来る",
      "休日に会ってくれない",
      "返信が早いのは会いたいときだけ"
    ];

    let current = 0;
    let score = 0;

    function answer(ans) {
      if (ans) score++;
      current++;
      const qtext = document.getElementById("qtext");

      if (current < questions.length) {
        qtext.textContent = questions[current];
      } else {
        document.getElementById("quiz").style.display = "none";
        showResult();
      }
    }

    function showResult() {
      const resultBox = document.getElementById("result");
      let text = "";
      let bg = "";

      if (score <= 2) {
        text = "🟢 安心ゾーン：今のところヤリモクの兆候は少なめです((( ´w｀ )))";
        bg = "#e6f4ea";
      } else if (score <= 5) {
        text = "🟡 やや怪しい：ちょっと気になる項目が出てきました。彡(^)(^)";
        bg = "#fff6d5";
      } else if (score <= 8) {
        text = "🟠 警戒ゾーン：かなり多くの“あるある”に該当しています…((( ´w｀ )))";
        bg = "#ffe7c8";
      } else {
        text = "🚨 高確率でヤリモク：これはヤリモク判定くんも真っ赤に反応しています🚨彡(^)(^)";
        bg = "#fce2e2";
      }

      resultBox.textContent = text;
      resultBox.style.background = bg;
    }
  </script>
</body>
</html>
