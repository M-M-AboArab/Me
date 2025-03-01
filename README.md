<!-- بداية قسم المصفوفة الخلفية -->
<canvas id="matrixCanvas"></canvas>

<!-- قسم الاختراق العشوائي -->
<div id="hackEffect" style="display:none; position:fixed; z-index:9999; text-align:center">
  <h1 style="
    color: #ff0000;
    font-size: 3em;
    text-shadow: 0 0 25px #ff0000;
    font-family: 'Courier New', monospace;
    animation: glitch 1s infinite;
  ">
    [ SYSTEM HACKED ]
  </h1>
</div>

<!-- بداية المحتوى الرئيسي -->
<div align="center" style="position:relative; z-index:2">
  
  <!-- أيقونة القفل النيونية -->
  <div style="margin:20px">
    <svg width="150" height="150" viewBox="0 0 24 24" style="filter: drop-shadow(0 0 15px #00ff88)">
      <path fill="#00ff88" d="M12 1C8.14 1 5 4.14 5 8v3c-1.65 0-3 1.35-3 3v7c0 1.65 1.35 3 3 3h14c1.65 0 3-1.35 3-3v-7c0-1.65-1.35-3-3-3V8c0-3.86-3.14-7-7-7zm0 2c2.76 0 5 2.24 5 5v3H7V8c0-2.76 2.24-5 5-5z"/>
    </svg>
  </div>

  <!-- روابط التواصل -->
  <div style="display:flex; gap:10px; margin:20px">
    <a href="https://wa.me/+201222606319" target="_blank">
      <img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white">
    </a>
    <a href="https://www.linkedin.com/in/mahmoud-mahmed-4b4884331" target="_blank">
      <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white">
    </a>
  </div>

</div>

<!-- محتوى الملف الأساسي -->
<div style="position:relative; z-index:2">
  
  ## 👤 About Me
  - 🎓 Cybersecurity Student  
  - 🌱 Currently learning: Ethical Hacking & Network Defense  
  - 🔒 Interests: Threat Intelligence • Cryptography • Pen Testing  

  ## 💻 Tech Stack
  ![](https://img.shields.io/badge/C++-00599C?style=flat&logo=c%2B%2B&logoColor=white)
  ![](https://img.shields.io/badge/SQL_Server-CC2927?style=flat&logo=microsoft-sql-server&logoColor=white)
  ![](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)

  ## 📊 GitHub Stats
  [![My Stats](https://github-readme-stats.vercel.app/api?username=M-M-AboArab&show_icons=true&theme=dark&bg_color=00000000)](https://github.com/M-M-AboArab)

  ## 💬 Random Cyber Quote
  <div id="quote-container" style="
    padding: 15px;
    margin: 20px 0;
    border-left: 3px solid #00ff88;
    background: rgba(0,0,0,0.3);
    font-family: 'Courier New', monospace;
  ">
    <p style="color: #00ff88; margin:0">"Security is a process, not a product"</p>
    <p style="color: #00ff88; margin:0; text-align:right">- Bruce Schneier</p>
  </div>

</div>

<!-- الأنيميشنات -->
<style>
  #matrixCanvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1;
    opacity: 0.3;
  }
  
  body {
    background: #000 !important;
    overflow-x: hidden;
  }

  /* تأثير الجليتش */
  @keyframes glitch {
    0% { text-shadow: 0 0 20px #ff0000; }
    25% { 
      text-shadow: 
        -5px -5px 0 #00ff88,
        5px 5px 0 #0000ff;
      transform: skew(10deg);
    }
    50% { 
      text-shadow: 
        0 0 30px #ff0000,
        0 0 15px #ffffff;
      transform: skew(-15deg);
    }
    100% { text-shadow: 0 0 20px #ff0000; }
  }
</style>

<script>
  // ========= Matrix Rain Effect =========
  const canvas = document.getElementById('matrixCanvas');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  const chars = '01@#$%&*ABCDEFGHJKLMNPRSTUVWXYZ';
  const drops = Array(Math.floor(canvas.width/8)).fill(0);

  function drawMatrix() {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.03)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = '#00ff88';
    ctx.font = '18px monospace';

    drops.forEach((drop, i) => {
      const text = chars[Math.floor(Math.random() * chars.length)];
      ctx.fillText(text, i*15, drop*15);
      if(drop*15 > canvas.height + Math.random()*1000) drops[i] = 0;
      drops[i]++;
    });
  }
  setInterval(drawMatrix, 50);

  // ========= نظام الاقتباسات =========
  const quotes = [
    {
      text: "The only secure system is one that is powered off",
      author: "Gene Spafford"
    },
    {
      text: "Privacy is not an option, it's a necessity",
      author: "Edward Snowden"
    },
    {
      text: "Hacking is not a crime, poor security is",
      author: "Unknown"
    }
  ];

  function updateQuote() {
    const quoteBox = document.getElementById('quote-container');
    const randomQuote = quotes[Math.floor(Math.random() * quotes.length)];
    quoteBox.innerHTML = `
      <p style="color: #00ff88; margin:0">"${randomQuote.text}"</p>
      <p style="color: #00ff88; margin:0; text-align:right">- ${randomQuote.author}</p>
    `;
  }
  setInterval(updateQuote, 10000);
  updateQuote();

  // ========= تأثير الاختراق =========
  setInterval(() => {
    document.getElementById('hackEffect').style.display = 'block';
    setTimeout(() => {
      document.getElementById('hackEffect').style.display = 'none';
    }, 2000);
  }, 30000);

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });
</script>
