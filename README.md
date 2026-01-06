<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Telegram Feed</title>

  <script src="https://telegram.org/js/telegram-web-app.js"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 16px;
      background: #ffffff;
    }
    .post {
      border-bottom: 1px solid #e0e0e0;
      padding: 12px 0;
    }
    .channel {
      font-weight: bold;
      color: #0088cc;
      margin-bottom: 4px;
    }
  </style>
</head>

<body>
  <h3>Лента каналов</h3>
  <div id="feed">Загрузка...</div>

  <script>
    if (window.Telegram && Telegram.WebApp) {
      Telegram.WebApp.ready();
      Telegram.WebApp.expand();
    }

    const posts = [
      { channel: "@telegram", text: "Обновление Telegram" },
      { channel: "@durov", text: "Пост Павла Дурова" }
    ];

    const feed = document.getElementById("feed");
    feed.innerHTML = "";

    posts.forEach(post => {
      const div = document.createElement("div");
      div.className = "post";
      div.innerHTML =
        '<div class="channel">' + post.channel + '</div>' +
        '<div>' + post.text + '</div>';
      feed.appendChild(div);
    });
  </script>
</body>
</html>
