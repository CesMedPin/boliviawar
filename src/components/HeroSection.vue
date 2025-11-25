<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

// Importamos el video del trailer para que Vite lo detecte bien
import trailerPath from '@/assets/media/fondo_guerra.mp4';

// --- LÓGICA DEL CARRUSEL ---
const currentImageIndex = ref(0);
let carouselInterval = null;

// TUS IMÁGENES (Asegúrate de que estén en la carpeta public/fondos/)
const images = [
  '/fondos/f1.jpg',
  '/fondos/f2.jpg',
  '/fondos/f3.jpg'
];

// --- LÓGICA DEL MODAL ---
const showModal = ref(false);

const openModal = () => {
  showModal.value = true;
  document.body.style.overflow = 'hidden';
};

const closeModal = () => {
  showModal.value = false;
  document.body.style.overflow = 'auto';
};

// --- CICLO DE VIDA ---
onMounted(() => {
  // Cambia la imagen cada 4 segundos
  carouselInterval = setInterval(() => {
    currentImageIndex.value = (currentImageIndex.value + 1) % images.length;
  }, 4000);
});

onUnmounted(() => {
  if (carouselInterval) clearInterval(carouselInterval);
});
</script>

<template>
  <div class="hero-wrapper">
    
    <!-- 1. CARRUSEL DE FONDO (VERSIÓN ROBUSTA CON <img>) -->
    <!-- Usamos <img> en lugar de div background para asegurar que carguen -->
    <div class="carousel-container">
      <img 
        v-for="(img, index) in images" 
        :key="index"
        :src="img"
        class="bg-slide"
        :class="{ active: index === currentImageIndex }"
        alt="Fondo de guerra"
      />
    </div>

    <!-- 2. CAPA OSCURA -->
    <div class="overlay"></div>

    <!-- 3. CONTENIDO PRINCIPAL -->
    <div class="content">
      <h2 class="subtitle">UN JUEGO DE ROBLOX</h2>
      <!-- TÍTULO CON FUENTE MILITAR -->
      <h1 class="title">BOLIVIA WARS</h1>
      
      <div class="badges">
        <span>GUERRA DEL CHACO</span>
        <span class="separator">•</span>
        <span>GUERRA DEL PACÍFICO</span>
      </div>

      <button @click="openModal" class="cta-button">
        VER TRÁILER
      </button>
    </div>

    <!-- 4. MODAL DEL TRÁILER -->
    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <button class="close-btn" @click="closeModal">✕</button>
        <video controls autoplay class="trailer-video">
             <source :src="trailerPath" type="video/mp4" />
             Tu navegador no soporta video.
        </video>
      </div>
    </div>

  </div>
</template>

<style scoped>
/* --- ESTRUCTURA --- */
.hero-wrapper {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  /* Fondo negro de seguridad por si tarda en cargar la imagen */
  background-color: #000; 
}

/* --- CARRUSEL --- */
.carousel-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    /* CORRECCIÓN: Usamos z-index positivo bajo (1) */
    z-index: 1;
}

.bg-slide {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover; /* IMPORTANTE: Hace que la imagen cubra todo sin deformarse */
    opacity: 0;
    transition: opacity 1s ease-in-out, transform 6s ease; /* Transición suave + zoom lento */
    transform: scale(1);
}

.bg-slide.active {
    opacity: 1;
    transform: scale(1.1); /* Efecto de zoom suave al estar activa */
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, rgba(0,0,0,0.2) 0%, rgba(0,0,0,0.8) 100%);
  /* CORRECCIÓN: Usamos z-index positivo medio (2) */
  z-index: 2;
}

/* --- TEXTOS --- */
.content {
  position: relative;
  /* CORRECCIÓN: Usamos z-index positivo alto (10) */
  z-index: 10;
  text-align: center;
  color: white;
  padding: 20px;
}

.subtitle {
  font-family: 'Roboto', sans-serif;
  font-size: 1.2rem;
  letter-spacing: 6px;
  margin-bottom: 15px;
  text-transform: uppercase;
  font-weight: 700;
  text-shadow: 0 2px 4px rgba(0,0,0,0.8);
}

.title {
  font-family: 'Black Ops One', cursive; /* FUENTE MILITAR */
  font-size: 6rem;
  margin: 0;
  text-transform: uppercase;
  letter-spacing: 2px;
  line-height: 0.9;
  text-shadow: 0 5px 20px rgba(0,0,0,0.8);
}

.badges {
  margin-top: 30px;
  font-size: 1.1rem;
  font-weight: bold;
  letter-spacing: 2px;
  text-transform: uppercase;
  text-shadow: 0 2px 4px rgba(0,0,0,0.8);
}

.separator {
  margin: 0 15px;
  color: #ffcc00;
}

/* --- BOTÓN --- */
.cta-button {
  margin-top: 50px;
  padding: 18px 50px;
  background-color: white;
  color: black;
  font-family: 'Black Ops One', cursive; /* Fuente militar */
  font-size: 1.2rem;
  border: none;
  cursor: pointer;
  text-transform: uppercase;
  letter-spacing: 2px;
  transition: all 0.2s ease;
  border: 3px solid white;
}

.cta-button:hover {
  background-color: transparent;
  color: white;
  transform: scale(1.05);
  text-shadow: 0 0 10px rgba(255,255,255,0.5);
}

/* --- MODAL --- */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.95);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  backdrop-filter: blur(5px);
}

.modal-content {
  position: relative;
  width: 90%;
  max-width: 1200px;
  aspect-ratio: 16 / 9;
  background: black;
  border: 1px solid #333;
  box-shadow: 0 0 50px rgba(255, 204, 0, 0.1);
}

.close-btn {
  position: absolute;
  top: -40px;
  right: 0;
  background: none;
  border: none;
  color: white;
  font-size: 2rem;
  cursor: pointer;
  transition: color 0.3s;
}

.close-btn:hover {
  color: #ffcc00;
}

.trailer-video {
  width: 100%;
  height: 100%;
  outline: none;
}

/* Responsive */
@media (max-width: 768px) {
  .title { font-size: 3.5rem; }
  .subtitle { font-size: 0.9rem; letter-spacing: 3px; }
  .cta-button { padding: 15px 30px; font-size: 1rem; }
  .close-btn { top: -35px; right: 5px; }
}
</style>