<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Repository Chatbot</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
  <script>
    async function askLLM() {
      const prompt = document.getElementById('prompt').value;
      const responseEl = document.getElementById('response');
      responseEl.innerHTML = 'Thinking...';

      const res = await fetch('https://YOUR_API_ENDPOINT', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({ prompt })
      });

      const data = await res.json();
      responseEl.innerHTML = marked.parse(data.response);
    }
  </script>
</head>
<body class="bg-gray-100 min-h-screen flex items-center justify-center">
  <div class="bg-white shadow-lg rounded-lg max-w-xl p-6 w-full">
    <h2 class="text-xl font-bold mb-4">Ask me anything about this repository!</h2>
    <input id="prompt" class="border rounded w-full p-2" placeholder="How do I install this?">
    <button onclick="askLLM()" class="bg-blue-500 text-white rounded mt-2 px-4 py-2">Submit</button>
    <div id="response" class="mt-4 prose"></div>
  </div>
</body>
</html>
