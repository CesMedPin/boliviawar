<script setup>
import { onMounted } from 'vue';
import HeroSection from './components/HeroSection.vue'
import MainContent from './components/MainContent.vue'

// --- LÓGICA DE ANIMACIÓN (SCROLL REVEAL) ---
// Este código hace que las secciones aparezcan mágicamente al bajar
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add('show');
      }
    });
  });

  // Esperamos un poco a que todo cargue y buscamos los elementos ocultos
  setTimeout(() => {
    const hiddenElements = document.querySelectorAll('.hidden');
    hiddenElements.forEach((el) => observer.observe(el));
  }, 100);
});
</script>

<template>
  <header class="navbar">
    <!-- Logo -->
    <a href="#" class="logo-link">
      <img src="@/assets/media/logo.png" alt="Bolivia Wars Logo" class="logo-img" />
    </a>
    
    <!-- Menú de Navegación -->
    <nav>
      <a href="#historia">Historia</a>
      <a href="#mapas">Mapas</a>
      <a href="#jugabilidad">Jugabilidad</a>
      <a href="#sobrenosotros">Sobre Nosotros</a>
    </nav>
  </header>

  <main>
    <HeroSection />
    <MainContent />
  </main>
</template>

<style>
/* --- 1. IMPORTAR FUENTE MILITAR --- */
@import url('https://fonts.googleapis.com/css2?family=Black+Ops+One&family=Roboto:wght@400;700&display=swap');

/* --- 2. CONFIGURACIÓN GLOBAL --- */
body {
  margin: 0;
  padding: 0;
  background-color: #050505;
  color: white;
  width: 100%;
  
  /* EL TRUCO DEL CURSOR: Cambia la flecha por una mira (+) */
  cursor: crosshair; 
  
  /* Fuente base para textos largos (párrafos) */
  font-family: 'Roboto', sans-serif;
}

/* Cambiar el cursor a 'mano' (pointer) en botones y enlaces */
a, button, .cta-button {
  cursor: pointer;
}

html {
  scroll-behavior: smooth;
}

/* --- 3. ESTILOS DE ANIMACIÓN --- */
/* Estado inicial: invisible y un poco más abajo */
.hidden {
  opacity: 0;
  transform: translateY(50px); /* Empujado hacia abajo */
  transition: all 1s ease-out; /* Transición suave de 1 segundo */
}

/* Estado final: visible y en su sitio */
.show {
  opacity: 1;
  transform: translateY(0);
}

/* --- NAVBAR FLOTANTE --- */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 15px 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 100;
  box-sizing: border-box;
  background: linear-gradient(to bottom, rgba(0,0,0,0.9) 0%, rgba(0,0,0,0) 100%);
  transition: background 0.3s;
}

.logo-img {
  height: 50px;
  width: auto;
  transition: transform 0.3s;
}
.logo-link:hover .logo-img { transform: scale(1.1); }

nav a {
  color: white;
  text-decoration: none;
  margin-left: 30px;
  font-family: 'Black Ops One', cursive; /* Fuente militar en menú */
  font-size: 1rem;
  letter-spacing: 1px;
  transition: color 0.3s;
  position: relative;
}

nav a:hover { color: #ffcc00; }

/* Ajuste Responsive para Navbar */
@media (max-width: 768px) {
  .navbar {
    padding: 10px 20px;
    flex-direction: column;
    background: rgba(0,0,0,0.95);
  }
  
  nav {
    margin-top: 15px;
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
    justify-content: center;
  }
  
  nav a {
    margin: 0;
    font-size: 0.8rem;
  }
}
</style>