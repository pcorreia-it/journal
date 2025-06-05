---
title: Paulo Correia's Journal
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<link href="https://fonts.googleapis.com/css2?family=Special+Elite&display=swap" rel="stylesheet">

<style>
  .social-links {
    position: fixed;
    top: 15px;
    right: 70px;
  }
  .social-links a {
    margin-left: 10px;
    font-size: 1.5rem;
    color: inherit;
  }
  body {
    font-family: 'Special Elite', monospace;
  }
  .intro {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 60vh;
    font-size: 2rem;
    font-weight: bold;
    text-align: center;
  }
  .links {
    text-align: center;
    margin-bottom: 2rem;
  }
  .links a {
    margin: 0 0.5rem;
  }
  </style>

<div class="social-links">
  <a href="https://www.instagram.com/pcorreia.it" target="_blank" rel="noopener" aria-label="Instagram">
    <i class="fab fa-instagram"></i>
  </a>
  <a href="https://github.com/pcorreia-it" target="_blank" rel="noopener" aria-label="GitHub">
    <i class="fab fa-github"></i>
  </a>
</div>

<div class="intro">
  Paulo <span id="typed"></span>
</div>

<div class="links">
  <a href="#projetos">#projetos</a>
  <a href="#pessoas">#pessoas</a>
  <a href="#lugares">#lugares</a>
  <a href="#eventos">#eventos</a>
  <a href="#ideias">#ideias</a>
</div>

<script>
document.addEventListener("DOMContentLoaded", () => {
  const words = ["é pai.", "é engenheiro.", "é marido.", "é brasileiro.", "é italiano.", "é músico."]; 
  let wordIndex = 0;
  let charIndex = 0;
  const typed = document.getElementById("typed");

  function type() {
    const word = words[wordIndex];
    if (charIndex <= word.length) {
      typed.textContent = word.slice(0, charIndex);
      charIndex++;
      setTimeout(type, 150);
    } else {
      setTimeout(erase, 1000);
    }
  }

  function erase() {
    const word = words[wordIndex];
    if (charIndex >= 0) {
      typed.textContent = word.slice(0, charIndex);
      charIndex--;
      setTimeout(erase, 100);
    } else {
      wordIndex = (wordIndex + 1) % words.length;
      setTimeout(type, 500);
    }
  }

  type();
});
</script>
