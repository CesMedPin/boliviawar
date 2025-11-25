<script setup>
// RUTAS DE TUS IMÁGENES
// Asegúrate de que los archivos estén en: public/contenido/
const imgHistoria = '/contenido/historia.jpg'; 
const imgMapa1 = '/contenido/mapa_boqueron.jpg';
const imgMapa2 = '/contenido/mapa_topater.jpg';
const imgJugabilidad = '/contenido/jugabilidad.jpg';
const imgStudio = '/contenido/logo_estudio.png';
</script>

<template>
  <div class="main-content">

    <!-- HISTORIA (Añadimos la clase 'hidden') -->
    <section id="historia" class="section split-section hidden">
      <div class="text-col">
        <h2 class="section-title">HISTORIA</h2>
        <h3 class="subtitle">ECOS DEL PASADO</h3>
        <p>
          Sumérgete en los conflictos más trascendentales de la historia de Bolivia. 
          Desde las áridas arenas de la Guerra del Pacífico hasta la densa vegetación del Chaco Boreal.
          Nuestra narrativa busca honrar la memoria de los caídos con una recreación respetuosa.
        </p>
      </div>
      <div class="img-col">
        <img :src="imgHistoria" alt="Historia" class="content-img shadow-box" />
      </div>
    </section>

    <!-- MAPAS (Añadimos la clase 'hidden') -->
    <section id="mapas" class="section maps-section hidden">
      <h2 class="section-title center-title">MAPAS ICÓNICOS</h2>
      
      <div class="maps-grid">
        <!-- A las tarjetas individuales también podemos ponerles 'hidden' para que salgan una por una -->
        <div class="map-card hidden" style="transition-delay: 200ms">
          <div class="map-img-container">
            <img :src="imgMapa1" alt="Mapa Boquerón" class="content-img" />
          </div>
          <h3>EL FORTÍN BOQUERÓN</h3>
          <p>Defiende el fortín contra probabilidades imposibles. Combate de infantería intenso.</p>
        </div>

        <div class="map-card hidden" style="transition-delay: 400ms">
          <div class="map-img-container">
            <img :src="imgMapa2" alt="Mapa Topáter" class="content-img" />
          </div>
          <h3>PUENTE DEL TOPÁTER</h3>
          <p>Un escenario abierto donde la defensa del puente es crucial. Ideal para francotiradores.</p>
        </div>
      </div>
    </section>

    <!-- JUGABILIDAD (Añadimos la clase 'hidden') -->
    <section id="jugabilidad" class="section split-section reverse hidden">
      <div class="img-col">
        <img :src="imgJugabilidad" alt="Gameplay" class="content-img shadow-box" />
      </div>
      <div class="text-col">
        <h2 class="section-title">JUGABILIDAD</h2>
        <h3 class="subtitle">REALISMO EN ROBLOX</h3>
        <p>
          Sistema de armas balísticas ajustado a la realidad. El cerrojo de los Mauser, 
          la recarga lenta de la artillería y la necesidad de trabajo en equipo son vitales.
        </p>
      </div>
    </section>

    <!-- SOBRE NOSOTROS (Añadimos la clase 'hidden') -->
    <section id="sobrenosotros" class="section split-section hidden">
      <div class="text-col">
        <h2 class="section-title">SOBRE NOSOTROS</h2>
        <h3 class="subtitle studio-name">PACEÑO STUDIO</h3>
        <p>
          Equipo independiente de desarrolladores bolivianos. Nuestro objetivo es educar 
          a través del entretenimiento en la plataforma global de Roblox.
        </p>
        
        <div class="social-links">
          <a href="#" class="social-btn">Facebook</a>
          <a href="#" class="social-btn">Twitter</a>
          <a href="#" class="social-btn">Discord</a>
        </div>
      </div>
      
      <div class="img-col">
        <img :src="imgStudio" alt="Paceño Studio" class="content-img logo-studio" />
      </div>
    </section>

    <footer class="footer">
      <p>&copy; 2025 Paceño Studio. Todos los derechos reservados.</p>
    </footer>

  </div>
</template>

<style scoped>
/* ESTILOS GENERALES */
.main-content {
  background-color: #050505;
  color: #fff;
  overflow: hidden; /* Importante para que las animaciones no creen barras de scroll lateral */
}

.section {
  padding: 100px 10%;
  border-bottom: 1px solid #1a1a1a;
}

/* APLICAMOS LA NUEVA FUENTE A LOS TÍTULOS */
.section-title {
  font-family: 'Black Ops One', cursive; /* <--- FUENTE MILITAR */
  font-size: 3.5rem;
  margin-bottom: 10px;
  text-transform: uppercase;
  color: #fff;
  line-height: 1;
  text-shadow: 2px 2px 0px #333; /* Sombra dura para efecto militar */
}

.subtitle {
  font-family: 'Roboto', sans-serif;
  color: #ffcc00;
  font-weight: 700;
  font-size: 1.2rem;
  margin-bottom: 30px;
  text-transform: uppercase;
  letter-spacing: 3px;
}

p {
  font-family: 'Roboto', sans-serif;
  color: #ccc;
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 20px;
}

.content-img {
  width: 100%;
  height: auto;
  border-radius: 2px;
  object-fit: cover;
  border: 1px solid #333; /* Borde sutil */
}

.shadow-box {
  box-shadow: 15px 15px 0px rgba(255, 204, 0, 0.1);
  transition: transform 0.3s;
}
.shadow-box:hover { transform: scale(1.02); }

/* LAYOUTS */
.split-section { display: flex; align-items: center; gap: 60px; }
.text-col, .img-col { flex: 1; }
.split-section.reverse { flex-direction: row-reverse; }

.center-title { text-align: center; margin-bottom: 60px; }
.maps-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 50px; }
.map-card h3 { 
  font-family: 'Black Ops One', cursive; 
  color: white; 
  margin: 15px 0 10px 0; 
  font-size: 1.5rem; 
}

/* REDES SOCIALES */
.studio-name { font-size: 2rem; color: #fff; text-decoration: underline #ffcc00; }
.social-links { display: flex; gap: 20px; margin-top: 30px; }
.social-btn {
  padding: 10px 20px;
  background: #1a1a1a;
  color: white;
  text-decoration: none;
  font-weight: bold;
  font-family: 'Black Ops One', cursive; /* Fuente militar en botones */
  border: 1px solid #333;
  transition: all 0.3s;
}
.social-btn:hover {
  background: #ffcc00;
  color: black;
  border-color: #ffcc00;
}

/* Footer */
.footer { text-align: center; padding: 40px; background: #000; color: #444; font-size: 0.9rem; }

/* Responsive */
@media (max-width: 900px) {
  .split-section, .split-section.reverse { flex-direction: column; text-align: center; }
  .maps-grid { grid-template-columns: 1fr; }
  .section-title { font-size: 2.5rem; }
}
</style>