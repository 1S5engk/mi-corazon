# Crear un archivo HTML personalizado con el nombre "Kathy"
html_content = """
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Para Kathy</title>
  <style>
    body {
      margin: 0;
      background: #1a001a;
      overflow: hidden;
      font-family: 'Segoe UI', sans-serif;
    }

    .heart {
      position: absolute;
      width: 10px;
      height: 10px;
      background: red;
      transform: rotate(45deg);
      animation: float 6s infinite ease-in-out;
    }

    .heart:before,
    .heart:after {
      content: '';
      position: absolute;
      width: 10px;
      height: 10px;
      background: inherit;
      border-radius: 50%;
    }

    .heart:before {
      top: -5px;
      left: 0;
    }

    .heart:after {
      left: -5px;
      top: 0;
    }

    @keyframes float {
      0% { transform: translateY(0) scale(1); opacity: 1; }
      100% { transform: translateY(-200px) scale(1.5); opacity: 0; }
    }

    .message {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: white;
      text-align: center;
      font-size: 2em;
      padding: 20px;
      animation: fadeIn 4s ease-in-out;
      max-width: 90%;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translate(-50%, -60%); }
      to { opacity: 1; transform: translate(-50%, -50%); }
    }
  </style>
</head>
<body>

<!-- Música romántica -->
<audio autoplay loop>
  <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
  Tu navegador no soporta el audio.
</audio>

<!-- Mensaje de amor -->
<div class="message">
  Kathy, te amo demasiado y gracias por llegar a mi vida.<br>
  Desde que te conozco soy mucho más feliz.
</div>

<script>
  function heartShape(t) {
    let x = 16 * Math.pow(Math.sin(t), 3);
    let y = 13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t);
    return { x, y };
  }

  const centerX = window.innerWidth / 2;
  const centerY = window.innerHeight / 2;
  const scale = 15;

  for (let i = 0; i < 500; i++) {
    const t = Math.random() * 2 * Math.PI;
    const { x, y } = heartShape(t);
    const heart = document.createElement('div');
    heart.className = 'heart';

    const color = Math.random() > 0.5 ? '#800080' : '#000000';
    heart.style.background = color;

    heart.style.left = ${centerX + x * scale + (Math.random() - 0.5) * 20}px;
    heart.style.top = ${centerY - y * scale + (Math.random() - 0.5) * 20}px;
    heart.style.animationDuration = ${2 + Math.random() * 4}s;

    document.body.appendChild(heart);
  }
</script>
</body>
</html>
"""

# Guardar el contenido en un archivo
file_path = "/mnt/data/index.html"
with open(file_path, "w", encoding="utf-8") as f:
    f.write(html_content)

file_path
