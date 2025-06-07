---
title: Journal
---

    <!-- Tailwind CSS for modern, responsive styling -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Google Font: 'Special Elite' -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Special+Elite&display=swap" rel="stylesheet">

    <style>
        /* Apply the custom font to the body */
        body {
            font-family: 'Special Elite', monospace;
        }
        /* Add a blinking cursor effect to the typed text */
        #typed-container::after {
            content: '|';
            display: inline-block;
            animation: blink 1s infinite;
        }
        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }
        /* Utility class to hide the element until the script is ready */
        .initially-hidden {
            opacity: 0;
        }
        /* Add a transition for the fade-in effect */
        #typed-container {
            transition: opacity 0.4s ease-in-out;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">

    <div class="container mx-auto px-4">
        <!-- Header / Social Links -->
        <header class="flex justify-end items-center py-6">
            <div class="social-links space-x-5">
                <a href="https://www.instagram.com/opaulohcorreia" target="_blank" rel="noopener" aria-label="Instagram" class="text-gray-500 hover:text-gray-900 transition-colors duration-300">
                    <i class="fab fa-instagram fa-lg"></i>
                </a>
                <a href="https://github.com/pcorreia-it" target="_blank" rel="noopener" aria-label="GitHub" class="text-gray-500 hover:text-gray-900 transition-colors duration-300">
                    <i class="fab fa-github fa-lg"></i>
                </a>
            </div>
        </header>

        <main>
            <!-- Introduction Section with Typing Animation -->
            <div class="flex justify-center items-center text-center" style="min-height: 50vh;">
                <!-- 'initially-hidden' class prevents content flash before fonts load -->
                <h1 id="typed-container" class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl font-bold text-gray-900 initially-hidden">
                    <span id="typed-prefix"></span><span id="typed"></span>
                </h1>
            </div>
            
            <!-- Navigation Links -->
            <div class="text-center mb-16 space-x-4 md:space-x-6">
                <a href="#projetos" class="text-gray-600 hover:text-blue-600 transition-colors">#projetos</a>
                <a href="#pessoas" class="text-gray-600 hover:text-blue-600 transition-colors">#pessoas</a>
                <a href="#lugares" class="text-gray-600 hover:text-blue-600 transition-colors">#lugares</a>
                <a href="#eventos" class="text-gray-600 hover:text-blue-600 transition-colors">#eventos</a>
                <a href="#ideias" class="text-gray-600 hover:text-blue-600 transition-colors">#ideias</a>
            </div>

            <!-- Content Sections for Anchor Links -->
            <div class="max-w-3xl mx-auto">
                <section id="projetos" class="mb-12">
                    <h2 class="text-3xl font-bold border-b-2 border-gray-200 pb-2 mb-4">Projetos</h2>
                    <p class="text-gray-700">Aqui você encontrará uma lista dos meus projetos... (Conteúdo de exemplo)</p>
                </section>
                <section id="pessoas" class="mb-12">
                    <h2 class="text-3xl font-bold border-b-2 border-gray-200 pb-2 mb-4">Pessoas</h2>
                    <p class="text-gray-700">Pessoas que me inspiram e com quem colaborei... (Conteúdo de exemplo)</p>
                </section>
                <section id="lugares" class="mb-12">
                    <h2 class="text-3xl font-bold border-b-2 border-gray-200 pb-2 mb-4">Lugares</h2>
                    <p class="text-gray-700">Lugares que visitei e que marcaram minha jornada... (Conteúdo de exemplo)</p>
                </section>
                 <section id="eventos" class="mb-12">
                    <h2 class="text-3xl font-bold border-b-2 border-gray-200 pb-2 mb-4">Eventos</h2>
                    <p class="text-gray-700">Eventos importantes e conferências que participei... (Conteúdo de exemplo)</p>
                </section>
                 <section id="ideias" class="mb-12">
                    <h2 class="text-3xl font-bold border-b-2 border-gray-200 pb-2 mb-4">Ideias</h2>
                    <p class="text-gray-700">Um repositório de pensamentos e ideias aleatórias... (Conteúdo de exemplo)</p>
                </section>
            </div>
        </main>
        
        <footer class="text-center py-8 text-gray-500 text-sm">
            <p>&copy; 2024 Paulo Correia. Feito com Jekyll e <span class="text-red-500">&hearts;</span>.</p>
        </footer>

    </div>

    <script>
    // Wait for the entire DOM to be parsed first.
    document.addEventListener("DOMContentLoaded", () => {
        const prefixText = "Paulo ";
        const words = ["é pai.", "é engenheiro.", "é marido.", "é brasileiro.", "é italiano.", "é músico.", "é pensador."];
        
        const typedContainerEl = document.getElementById("typed-container");
        const typedPrefixEl = document.getElementById("typed-prefix");
        const typedEl = document.getElementById("typed");

        // Set the initial state of the text immediately
        typedPrefixEl.textContent = prefixText;
        typedEl.textContent = "";

        // Wait until all fonts in the document are loaded and ready.
        // This is the key to preventing the flicker.
        document.fonts.ready.then(() => {
            // Now that fonts are ready, make the container visible.
            typedContainerEl.classList.remove('initially-hidden');
            
            // Start the typing effect.
            typeEffect();
        });

        let wordIndex = 0;
        let charIndex = 0;
        let isErasing = false;

        // Configuration for timing
        const typeSpeed = 150;
        const eraseSpeed = 100;
        const delayAfterTyping = 1500;
        const delayAfterErasing = 300;

        function typeEffect() {
            const currentWord = words[wordIndex];
            
            if (isErasing) {
                // Handle erasing
                typedEl.textContent = currentWord.slice(0, charIndex--);
                if (charIndex < 0) {
                    isErasing = false;
                    wordIndex = (wordIndex + 1) % words.length;
                    setTimeout(typeEffect, delayAfterErasing);
                } else {
                    setTimeout(typeEffect, eraseSpeed);
                }
            } else {
                // Handle typing
                typedEl.textContent = currentWord.slice(0, ++charIndex);
                if (charIndex > currentWord.length) {
                    isErasing = true;
                    setTimeout(typeEffect, delayAfterTyping);
                } else {
                    setTimeout(typeEffect, typeSpeed);
                }
            }
        }
    });
    </script>

