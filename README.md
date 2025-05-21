<html>
<head>
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
</head>
<body>
<h2>Ask Me About This Repo!</h2>
<input type="text" id="prompt" placeholder="How do I install this?" />
<button onclick="askLLM()">Ask</button>
<div id="response"></div>

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
</body>
</html>
