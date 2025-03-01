<!-- بداية قسم المصفوفة الخلفية -->
<canvas id="matrixCanvas"></canvas>

<!-- المحتوى الرئيسي -->
<div align="center" style="position:relative; z-index:2">
  <!-- ... (المحتوى الأصلي بدون تغيير) ... -->
</div>

<!-- أنيميشن المصفوفة -->
<style>
  #matrixCanvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1;
    opacity: 0.15;
  }
  
  body {
    background: #000 !important;
  }
</style>

<script>
  // Matrix Rain Effect
  const canvas = document.getElementById('matrixCanvas');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%^&*()';
  const drops = Array(Math.floor(canvas.width/10)).fill(0);

  function drawMatrix() {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = '#0F0';
    ctx.font = '12px monospace';

    drops.forEach((drop, i) => {
      const text = chars[Math.floor(Math.random() * chars.length)];
      ctx.fillText(text, i*10, drop*10);
      if(drop*10 > canvas.height || Math.random() > 0.975) drops[i] = 0;
      drops[i]++;
    });
  }
  setInterval(drawMatrix, 50);

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });
</script>
