<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import trailerPath from '@/assets/media/fondo_guerra.mp4';

// CONFIGURACIÓN
const currentImageIndex = ref(0);
let carouselInterval = null;

// RUTAS DIRECTAS (Asegúrate que coincidan con tus archivos en public/fondos/)
const images = [
  '/fondos/f1.jpg',
  '/fondos/f2.jpg',
  '/fondos/f3.jpg'
];

// MODAL
const showModal = ref(false);
const openModal = () => { showModal.value = true; document.body.style.overflow = 'hidden'; };
const closeModal = () => { showModal.value = false; document.body.style.overflow = 'auto'; };

// INTERVALO
onMounted(() => {
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
    
    <div class="carousel-container">
      <img 
        v-for="(img, index) in images" 
        :key="index"
        :src="img"
        class="bg-img"
        :class="{ active: index === currentImageIndex }"
        alt="Fondo de guerra"
      />
    </div>

    <div class="overlay"></div>

    <div class="content">
      <h2 class="subtitle">UN JUEGO DE ROBLOX</h2>
      <h1 class="title">BOLIVIA WARS</h1>
      
      <div class="badges">
        <span>GUERRA DEL CHACO</span>
        <span class="separator">•</span>
        <span>GUERRA DEL PACÍFICO</span>
      </div>

      <button @click="openModal" class="cta-button">VER TRÁILER</button>
    </div>

    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <button class="close-btn" @click="closeModal">✕</button>
        <video controls autoplay class="trailer-video">
             <source :src="trailerPath" type="video/mp4" />
        </video>
      </div>
    </div>

  </div>
</template>

<style scoped>
.hero-wrapper {
  position: relative;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  background-color: #000;
}

/* --- ESTILOS NUEVOS PARA LAS IMÁGENES --- */
.carousel-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0; /* Al fondo */
}

.bg-img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover; /* Clave: hace que la imagen rellene todo sin deformarse */
  opacity: 0;
  transition: opacity 1.5s ease-in-out, transform 6s ease;
  transform: scale(1);
}

.bg-img.active {
  opacity: 1;
  transform: scale(1.1); /* Efecto zoom suave */
}

/* Capa oscura encima de las fotos pero debajo del texto */
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5); /* 50% oscuridad */
  z-index: 1;
}

.content {
  position: relative;
  z-index: 2; /* Encima de todo */
  text-align: center;
  color: white;
  font-family: 'Arial Black', sans-serif;
}

/* ... RESTO DE ESTILOS IGUAL QUE ANTES ... */
.subtitle {
  font-size: 1.2rem;
  letter-spacing: 6px;
  margin-bottom: 15px;
  text-transform: uppercase;
}

.title {
  font-size: 6rem;
  margin: 0;
  text-transform: uppercase;
  letter-spacing: -2px;
  line-height: 0.9;
}

.badges { margin-top: 30px; font-weight: bold; letter-spacing: 2px; }
.separator { margin: 0 15px; color: #ffcc00; }

.cta-button {
  margin-top: 50px;
  padding: 18px 50px;
  background-color: white;
  color: black;
  font-weight: bold;
  border: 3px solid white;
  cursor: pointer;
  text-transform: uppercase;
  transition: 0.3s;
}
.cta-button:hover { background: transparent; color: white; transform: scale(1.05); }

/* Modal */
.modal-overlay {
  position: fixed;
  top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(0,0,0,0.9);
  z-index: 999;
  display: flex; justify-content: center; align-items: center;
}
.modal-content { width: 90%; max-width: 1000px; aspect-ratio: 16/9; background: black; position: relative; }
.close-btn { position: absolute; top: -40px; right: 0; background: none; border: none; color: white; font-size: 2rem; cursor: pointer; }
.trailer-video { width: 100%; height: 100%; }

@media (max-width: 768px) { .title { font-size: 3.5rem; } }
</style>