---
title: Paulo Correia's Journal
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

<style>
  .social-links {
    position: fixed;
    top: 10px;
    right: 10px;
  }
  .social-links a {
    margin-left: 10px;
    font-size: 1.5rem;
    color: inherit;
  }
  .intro {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 80vh;
    font-size: 2rem;
    font-weight: bold;
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
