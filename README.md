# KSM-Zeitlarn.github.io
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Text an PC senden</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 2rem;
      background-color: #f4f4f4;
      color: #333;
    }
    .container {
      max-width: 600px;
      margin: auto;
      background: white;
      padding: 2rem;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    textarea {
      width: 100%;
      height: 200px;
      padding: 1rem;
      font-size: 1rem;
      border-radius: 5px;
      border: 1px solid #ccc;
      resize: vertical;
    }
    button {
      margin-top: 1rem;
      padding: 0.75rem 1.5rem;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 1rem;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .message {
      margin-top: 1rem;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Text an PC senden</h2>
    <form id="textForm">
      <textarea id="textInput" name="text" placeholder="Schreibe hier deinen Text..."></textarea>
      <button type="submit">Senden</button>
    </form>
    <div class="message" id="message"></div>
  </div>

  <script>
    const form = document.getElementById('textForm');
    const message = document.getElementById('message');

    form.addEventListener('submit', async (e) => {
      e.preventDefault();

      const text = document.getElementById('textInput').value;
      const formData = new FormData();
      formData.append('text', text);

      try {
        const response = await fetch('https://funny-monkey-example.trycloudflare.com/submit', {
          method: 'POST',
          body: formData
        });

        const result = await response.text();
        message.textContent = result;
      } catch (error) {
        message.textContent = 'Fehler beim Senden.';
        console.error(error);
      }
    });
  </script>
</body>
</html>
