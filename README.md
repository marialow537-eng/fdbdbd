<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Создание репозитория GitHub</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 40px; }
        pre { background: #f4f4f4; padding: 20px; border-radius: 8px; }
        button { padding: 10px 20px; font-size: 16px; cursor: pointer; }
    </style>
</head>
<body>

<h1>Создание нового репозитория на GitHub</h1>

<button onclick="createRepo()">Создать репозиторий</button>

<pre id="output">Нажми кнопку, чтобы создать репозиторий.</pre>

<script>
// РАНДОМНОЕ имя репозитория
function randomRepoName() {
    const words = ["alpha", "beta", "gamma", "omega", "fusion", "nova", "pixel", "quantum"];
    const num = Math.floor(Math.random() * 10000);
    return words[Math.floor(Math.random() * words.length)] + "-" + num;
}

async function createRepo() {
    const repoName = randomRepoName();

    const token = "YOUR_GITHUB_TOKEN_HERE"; // вставь свой токен

    const data = {
        name: repoName,
        description: "Auto-created repo via GitHub API",
        private: false
    };

    const response = await fetch("https://api.github.com/user/repos", {
        method: "POST",
        headers: {
            "Authorization": "token " + token,
            "Accept": "application/vnd.github+json"
        },
        body: JSON.stringify(data)
    });

    const result = await response.json();
    document.getElementById("output").textContent = JSON.stringify(result, null, 2);
}
</script>

</body>
</html>
