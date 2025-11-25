<script setup>
import HeroSection from './components/HeroSection.vue'
import MainContent from './components/MainContent.vue' // Importamos el nuevo componente
</script>

<template>
  <header class="navbar">
    <!-- Logo -->
    <a href="#" class="logo-link">
      <img src="@/assets/media/logo.png" alt="Bolivia Wars Logo" class="logo-img" />
    </a>
    
    <!-- Menú de Navegación -->
    <nav>
      <!-- Los href con #id permiten viajar a esa parte de la página -->
      <a href="#historia">Historia</a>
      <a href="#mapas">Mapas</a>
      <a href="#jugabilidad">Jugabilidad</a>
      <a href="#sobrenosotros">Sobre Nosotros</a>
    </nav>
  </header>

  <main>
    <HeroSection />
    <MainContent /> <!-- Aquí cargamos todo el contenido nuevo -->
  </main>
</template>

<style>
/* --- ESTILOS GLOBALES --- */
html {
  /* ESTO ES MAGIA: Hace que el scroll sea suave al pulsar los botones */
  scroll-behavior: smooth;
}

body {
  margin: 0;
  padding: 0;
  background-color: #000;
  color: white;
  width: 100%;
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
  /* Fondo con degradado para que se lea bien sobre cualquier imagen */
  background: linear-gradient(to bottom, rgba(0,0,0,0.9) 0%, rgba(0,0,0,0) 100%);
  transition: background 0.3s;
}

/* Opcional: Si quieres que la barra se ponga negra al bajar,
   se requiere un poco de JS, pero por ahora el degradado funciona bien. */

.navbar:hover {
    background: rgba(0,0,0,0.9);
}

.logo-img {
  height: 50px;
  width: auto;
  transition: transform 0.3s;
}

.logo-link:hover .logo-img {
  transform: scale(1.1);
}

nav a {
  color: white;
  text-decoration: none;
  margin-left: 30px;
  font-family: sans-serif;
  font-weight: bold;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 1px;
  transition: color 0.3s;
  position: relative;
}

nav a:hover {
  color: #ffcc00;
}

/* Efecto de línea debajo al pasar el mouse */
nav a::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: -5px;
  left: 0;
  background-color: #ffcc00;
  transition: width 0.3s;
}

nav a:hover::after {
  width: 100%;
}

/* Ajuste Responsive para Navbar */
@media (max-width: 768px) {
  .navbar {
    padding: 10px 20px;
    flex-direction: column;
    background: rgba(0,0,0,0.9); /* Fondo sólido en móviles */
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
    font-size: 0.7rem;
  }
}
</style>