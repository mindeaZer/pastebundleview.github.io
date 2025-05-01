<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>ZipGenie - AI File Packager</title>
  <style>
    /* Animated gradient background */
    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(-45deg, #0f2027, #203a43, #2c5364, #4b6cb7);
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
      color: #eef;
    }
    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    .container {
      max-width: 800px;
      margin: auto;
      padding: 2rem;
      backdrop-filter: blur(10px);
    }
    h1 {
      text-align: center;
      font-size: 2.5rem;
      margin-bottom: 0.2rem;
    }
    .subtitle {
      text-align: center;
      font-size: 1.2rem;
      margin-bottom: 2rem;
      opacity: 0.8;
    }
    /* Logo placeholder (static) */
    .logo-placeholder {
      width: 150px;
      height: 150px;
      margin: 1rem auto;
      border: 2px dashed #eef;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
    }
    /* Editor styles */
    .editor {
      margin-bottom: 1.5rem;
    }
    label {
      display: block;
      margin-bottom: 0.5rem;
      font-weight: bold;
    }
    textarea {
      width: 100%;
      height: 150px;
      font-family: monospace;
      font-size: 0.9rem;
      padding: 0.5rem;
      background: rgba(0,0,0,0.6);
      color: #eef;
      border: 1px solid #447;
      border-radius: 4px;
      resize: vertical;
    }
    button {
      display: block;
      margin: 1rem auto;
      padding: 0.75rem 1.5rem;
      font-size: 1rem;
      cursor: pointer;
      background: rgba(255,255,255,0.1);
      border: 1px solid #eef;
      border-radius: 4px;
      transition: transform 0.2s, box-shadow 0.2s;
    }
    button:hover {
      transform: scale(1.05);
      box-shadow: 0 0 10px #eef;
    }
    /* Features section */
    .features {
      margin-top: 3rem;
    }
    .features h2 {
      text-align: center;
      margin-bottom: 1rem;
    }
    .features ul {
      list-style: none;
      padding: 0;
    }
    .features li {
      margin: 0.5rem 0;
      padding: 0.5rem;
      background: rgba(255,255,255,0.1);
      border-radius: 4px;
      backdrop-filter: blur(5px);
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>ZipGenie</h1>
    <div class="subtitle">AI-powered bundler for HTML, CSS & Java – package it fast!</div>
    <div class="logo-placeholder">Your Logo Here</div>
    
    <div class="editor">
      <label for="htmlContent">HTML (index.html):</label>
      <textarea id="htmlContent" placeholder="Paste your index.html here"></textarea>
    </div>
    <div class="editor">
      <label for="cssContent">CSS (style.css):</label>
      <textarea id="cssContent" placeholder="Paste your style.css here"></textarea>
    </div>
    <div class="editor">
      <label for="javaContent">Java (Main.java):</label>
      <textarea id="javaContent" placeholder="Paste your Main.java here"></textarea>
    </div>
    <button id="generateBtn">Generate Package</button>
    
    <div class="features">
      <h2>Features</h2>
      <ul>
        <li>Instant folder & file creation</li>
        <li>Randomized folder names for uniqueness</li>
        <li>Download a ready-to-unzip ZIP in one click</li>
        <li>Lightweight, client-side, no server needed</li>
        <li>Open source & easily customizable</li>
      </ul>
    </div>
  </div>
  
  <!-- Libraries -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.0/jszip.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.5/FileSaver.min.js"></script>
  <script>
    document.getElementById('generateBtn').addEventListener('click', () => {
      const zip = new JSZip();
      const folderName = Math.random().toString(36).substring(2,8);
      const folder = zip.folder(folderName);
      const html = document.getElementById('htmlContent').value;
      const css  = document.getElementById('cssContent').value;
      const java = document.getElementById('javaContent').value;
      folder.file('index.html', html);
      folder.file('style.css', css);
      folder.file('Main.java', java);
      zip.generateAsync({ type: 'blob' })
         .then(blob => saveAs(blob, `${folderName}.zip`));
    });
  </script>
</body>
</html>

