<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>MindStack Home</title>
  <style>
    /* Navigation bar styles */
    nav {
      background: #1e1e1e;
      padding: 10px 20px;
      display: flex;
      gap: 20px;
      justify-content: center;
      box-shadow: 0 2px 5px rgba(0,0,0,0.7);
      position: sticky;
      top: 0;
      z-index: 100;
    }

    nav a {
      color: #eee;
      text-decoration: none;
      font-weight: 600;
      font-size: 1.1rem;
      transition: color 0.3s ease;
      padding: 8px 12px;
      border-radius: 6px;
      user-select: none;
    }

    nav a:hover {
      color: #4caf50;
      background: rgba(76, 175, 80, 0.15);
    }

    /* Dark theme for body */
    body {
      margin: 0;
      background: #121212;
      color: #eee;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
      padding: 20px;
      overflow: hidden;
    }

    /* The welcome message style */
    .welcome {
      position: relative;
      font-size: 3rem;
      font-weight: 900;
      text-align: center;
      max-width: 90vw;
      line-height: 1.2;
      color: #4caf50;
      user-select: none;
      cursor: pointer;
      letter-spacing: 1.5px;
      /* Glossy text effect */
      background: linear-gradient(45deg, #81c784, #388e3c);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow:
        0 0 5px #4caf50,
        0 0 10px #4caf50,
        0 0 20px #81c784,
        0 0 40px #388e3c;
      overflow: hidden;
    }

    /* Ripple container */
    .ripple {
      position: absolute;
      border-radius: 50%;
      transform: scale(0);
      animation: ripple-effect 600ms linear;
      background-color: rgba(76, 175, 80, 0.4);
      pointer-events: none;
      mix-blend-mode: screen;
      z-index: 1;
    }

    @keyframes ripple-effect {
      to {
        transform: scale(4);
        opacity: 0;
      }
    }

  </style>
</head>
<body>

<nav>
  <a href="index.html">Home</a>
  <a href="flashcards.html">Flashcards</a>
</nav>

<h1 class="welcome" id="welcomeText">Welcome to MindStack,<br>the free flashcard website</h1>

<script>
  const welcomeText = document.getElementById('welcomeText');

  welcomeText.addEventListener('click', e => {
    const rect = welcomeText.getBoundingClientRect();

    // Create ripple element
    const ripple = document.createElement('span');
    ripple.classList.add('ripple');

    // Calculate click position relative to the element
    const size = Math.max(rect.width, rect.height);
    ripple.style.width = ripple.style.height = size + 'px';
    ripple.style.left = (e.clientX - rect.left - size / 2) + 'px';
    ripple.style.top = (e.clientY - rect.top - size / 2) + 'px';

    welcomeText.appendChild(ripple);

    // Remove ripple after animation
    ripple.addEventListener('animationend', () => {
      ripple.remove();
    });
  });
</script>

</body>
</html>
