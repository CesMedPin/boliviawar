<script setup>
// Aquí definimos rutas a imágenes temporales. 
// Cuando tengas las fotos finales, reemplaza '/fondos/f1.jpg' por la ruta real.
const imgHistoria = '/contenido/historia.jpg'; 
const imgMapa1 = '/contenido/mapa_boqueron.jpg';
const imgMapa2 = '/contenido/mapa_topater.jpg';
const imgJugabilidad = '/contenido/jugabilidad.jpg';
const imgStudio = '/contenido/logo_estudio.png';
</script>

<template>
  <div class="main-content">

    <!-- 1. SECCIÓN HISTORIA (Texto Izquierda / Imagen Derecha) -->
    <section id="historia" class="section split-section">
      <div class="text-col">
        <h2 class="section-title">HISTORIA</h2>
        <h3 class="subtitle">ECOS DEL PASADO</h3>
        <p>
          Sumérgete en los conflictos más trascendentales de la historia de Bolivia. 
          Desde las áridas arenas de la Guerra del Pacífico hasta la densa vegetación del Chaco Boreal.
          Nuestra narrativa busca honrar la memoria de los caídos con una recreación respetuosa y 
          documentada, permitiendo a las nuevas generaciones vivir la historia en primera persona.
        </p>
      </div>
      <div class="img-col">
        <img :src="imgHistoria" alt="Historia de la guerra" class="content-img shadow-box" />
      </div>
    </section>

    <!-- 2. SECCIÓN MAPAS (2 Columnas: Imagen arriba, Texto abajo) -->
    <section id="mapas" class="section maps-section">
      <h2 class="section-title center-title">MAPAS ICÓNICOS</h2>
      
      <div class="maps-grid">
        <!-- Mapa 1 -->
        <div class="map-card">
          <div class="map-img-container">
            <img :src="imgMapa1" alt="Mapa Boquerón" class="content-img" />
          </div>
          <h3>EL FORTÍN BOQUERÓN</h3>
          <p>
            Defiende el fortín contra probabilidades imposibles. Un mapa cerrado diseñado para 
            el combate de infantería intenso y la resistencia estratégica.
          </p>
        </div>

        <!-- Mapa 2 -->
        <div class="map-card">
          <div class="map-img-container">
            <img :src="imgMapa2" alt="Mapa Topáter" class="content-img" />
          </div>
          <h3>PUENTE DEL TOPÁTER</h3>
          <p>
            Un escenario abierto donde la defensa del puente es crucial. Ideal para francotiradores 
            y emboscadas tácticas en terreno desértico.
          </p>
        </div>
      </div>
    </section>

    <!-- 3. SECCIÓN JUGABILIDAD (Imagen Izquierda / Texto Derecha) -->
    <section id="jugabilidad" class="section split-section reverse">
      <div class="img-col">
        <img :src="imgJugabilidad" alt="Gameplay Roblox" class="content-img shadow-box" />
      </div>
      <div class="text-col">
        <h2 class="section-title">JUGABILIDAD</h2>
        <h3 class="subtitle">MECÁNICAS REALISTAS EN ROBLOX</h3>
        <p>
          Experimenta un sistema de armas balísticas ajustado a la realidad de la época. 
          El cerrojo de los Mauser, la recarga lenta de la artillería y la necesidad de 
          trabajo en equipo son vitales. No es solo disparar; es sobrevivir, suministrar 
          munición y mantener la línea de frente junto a tu escuadrón.
        </p>
      </div>
    </section>

    <!-- 4. SECCIÓN SOBRE NOSOTROS (Texto + Redes Izquierda / Imagen Derecha) -->
    <section id="sobrenosotros" class="section split-section">
      <div class="text-col">
        <h2 class="section-title">SOBRE NOSOTROS</h2>
        <h3 class="subtitle studio-name">PACEÑO STUDIO</h3>
        <p>
          Somos un equipo independiente de desarrolladores bolivianos apasionados por la historia y los videojuegos. 
          Nuestro objetivo es educar a través del entretenimiento, llevando nuestras historias a la plataforma global de Roblox.
        </p>
        
        <!-- REDES SOCIALES -->
        <div class="social-links">
          <a href="#" class="social-btn facebook">
            <!-- Icono Facebook SVG -->
            <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path></svg>
            Facebook
          </a>
          <a href="#" class="social-btn twitter">
            <!-- Icono X/Twitter SVG -->
            <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"><path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"></path></svg>
            Twitter
          </a>
          <a href="#" class="social-btn discord">
            <!-- Icono Discord SVG -->
            <svg viewBox="0 0 24 24" width="24" height="24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"><path d="M21 11.5a8.38 8.38 0 0 1-.9 3.8 8.5 8.5 0 0 1-7.6 4.7 8.38 8.38 0 0 1-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 0 1-.9-3.8 8.5 8.5 0 0 1 4.7-7.6 8.38 8.38 0 0 1 3.8-.9h.5a8.48 8.48 0 0 1 8 8v.5z"></path></svg>
            Discord
          </a>
        </div>
      </div>
      
      <div class="img-col">
        <img :src="imgStudio" alt="Paceño Studio Logo" class="content-img logo-studio" />
      </div>
    </section>

    <!-- Footer Simple -->
    <footer class="footer">
      <p>&copy; 2024 Paceño Studio. Todos los derechos reservados.</p>
    </footer>

  </div>
</template>

<style scoped>
/* ESTILOS GENERALES */
.main-content {
  background-color: #050505; /* Casi negro */
  color: #fff;
  font-family: sans-serif;
}

.section {
  padding: 100px 10%; /* Mucho espacio arriba/abajo y a los lados */
  border-bottom: 1px solid #222; /* Línea sutil separadora */
}

.section-title {
  font-family: 'Arial Black', sans-serif;
  font-size: 3.5rem;
  margin-bottom: 10px;
  text-transform: uppercase;
  color: #fff;
  line-height: 1;
}

.subtitle {
  font-family: 'Arial Black', sans-serif;
  color: #ffcc00; /* Amarillo Boliviano */
  font-size: 1.5rem;
  margin-bottom: 30px;
  text-transform: uppercase;
  letter-spacing: 2px;
}

p {
  color: #ccc;
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 20px;
}

.content-img {
  width: 100%;
  height: auto;
  border-radius: 4px;
  object-fit: cover;
}

/* Efecto de sombra para imágenes destacadas */
.shadow-box {
  box-shadow: 20px 20px 0px rgba(255, 204, 0, 0.1);
  transition: transform 0.3s;
}
.shadow-box:hover {
  transform: scale(1.02);
}

/* --- ESTILOS PARA SECCIONES DIVIDIDAS (IZQ/DER) --- */
.split-section {
  display: flex;
  align-items: center;
  gap: 60px;
}

.text-col, .img-col {
  flex: 1; /* Ocupan 50% cada uno */
}

/* Para invertir el orden en "Jugabilidad" */
.split-section.reverse {
  flex-direction: row-reverse;
}

/* --- ESTILOS PARA SECCIÓN MAPAS (COLUMNAS) --- */
.center-title {
  text-align: center;
  margin-bottom: 60px;
}

.maps-grid {
  display: grid;
  grid-template-columns: 1fr 1fr; /* 2 Columnas iguales */
  gap: 50px;
}

.map-card {
  text-align: left;
}

.map-img-container {
  overflow: hidden;
  margin-bottom: 25px;
  border: 1px solid #333;
}

.map-card h3 {
  font-family: 'Arial Black', sans-serif;
  color: white;
  margin-bottom: 10px;
  font-size: 1.5rem;
}

/* --- ESTILOS REDES SOCIALES --- */
.studio-name {
  font-size: 2rem;
  color: #fff;
  text-decoration: underline #ffcc00;
}

.social-links {
  display: flex;
  gap: 20px;
  margin-top: 30px;
}

.social-btn {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 20px;
  background: #222;
  color: white;
  text-decoration: none;
  font-weight: bold;
  border-radius: 5px;
  transition: background 0.3s, color 0.3s;
}

.social-btn:hover {
  background: #ffcc00;
  color: black;
}

/* Responsive para móviles */
@media (max-width: 900px) {
  .split-section, .split-section.reverse {
    flex-direction: column;
    text-align: center;
  }
  
  .maps-grid {
    grid-template-columns: 1fr; /* 1 Columna en móvil */
  }

  .section-title {
    font-size: 2.5rem;
  }
}

.footer {
  text-align: center;
  padding: 40px;
  background: #000;
  color: #666;
  font-size: 0.9rem;
}
</style>