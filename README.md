<!-- بداية قسم المصفوفة الخلفية -->
<canvas id="matrixCanvas"></canvas>

<!-- بداية قسم المحتوى الرئيسي -->
<div align="center" style="position:relative; z-index:2">
  
  <!-- أيقونة القفل النيونية -->
  <div style="margin:20px">
    <svg width="100" height="100" viewBox="0 0 24 24" style="filter: drop-shadow(0 0 10px #00ff88)">
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
  
  ## About Me
  - 🎓 Cybersecurity Student
  - 🌱 Currently learning: Ethical Hacking & Network Defense
  - 🔒 Interests: Threat Intelligence • Cryptography • Penetration Testing

  ## Tech Stack
  ![](https://img.shields.io/badge/C++-00599C?style=flat&logo=c%2B%2B&logoColor=white)
  ![](https://img.shields.io/badge/SQL_Server-CC2927?style=flat&logo=microsoft-sql-server&logoColor=white)
  ![](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)

  ## GitHub Stats
  [![My Stats](https://github-readme-stats.vercel.app/api?username=M-M-AboArab&show_icons=true&theme=dark&bg_color=00000000)](https://github.com/M-M-AboArab)

  ## ✍️ Random Dev Quote
  <div id="quote-container"></div>

</div>

<!-- أنيميشن المصفوفة -->
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
    overflow: hidden;
  }

  #quote-container {
    padding: 20px;
    margin: 20px 0;
    border-left: 3px solid #00ff88;
    background: rgba(0, 0, 0, 0.3);
    font-family: 'Courier New', monospace;
    color: #00ff88;
  }
</style>

<script>
  // Matrix Rain Effect
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

  // نظام الاقتباسات العشوائية
  const quotes = [
    {
      text: "Security is a process, not a product.",
      author: "Bruce Schneier"
    },
    {
      text: "The only secure system is one that is powered off.",
      author: "Gene Spafford"
    },
    {
      text: "Privacy is not an option, and it shouldn't be the price we accept for connectivity.",
      author: "Aral Balkan"
    }
  ];

  function updateQuote() {
    const quote = quotes[Math.floor(Math.random() * quotes.length)];
    const quoteElement = document.getElementById('quote-container');
    quoteElement.innerHTML = `
      <p>"${quote.text}"</p>
      <p><strong>— ${quote.author}</strong></p>
    `;
  }

  // تحديث الاقتباس كل 10 ثوانٍ
  setInterval(updateQuote, 10000);
  updateQuote(); // التحميل الأولي

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  });
</script>
