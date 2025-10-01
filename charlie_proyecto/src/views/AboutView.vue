<template>
  <section class="charlie-about">
    <!-- Hero Section con Logo Pequeño y Estético -->
    <div class="hero">
      <div class="hero-content">
        <div class="logo-wrapper">
          <img src="@/assets/Logo charlie.png" alt="Charlie Boys - Pizza & Grill" class="logo" />
        </div>
        <div class="text-content">
          <h1 class="brand">Sobre Charlie Boys</h1>
          <p class="tag">Más que hamburguesas: una pasión por sabores auténticos</p>
          <div class="hero-ctas">
            <router-link to="/menu" class="btn primary">Ver Menú</router-link>
            <router-link to="/about" class="btn outline">Sobre Nosotros</router-link>
          </div>
        </div>
      </div>
    </div>

    <!-- Historia -->
    <div class="section historia">
      <div class="container">
        <h2 class="title">Nuestra Historia</h2>
        <div class="history-text">
          <p>
            <strong>Charlie Boys nació en El Salvador en los años 2000</strong> con un sueño simple: ofrecer hamburguesas jugosas, hechas con ingredientes frescos y preparadas con amor.
          </p>
          <p>
            Desde entonces, nos hemos convertido en un referente de la comida rápida de calidad en todo el país. Hoy contamos con múltiples sucursales y seguimos creciendo, siempre comprometidos con el sabor, la calidad y la experiencia de nuestros clientes.
          </p>
          <p class="motto">
            Porque no solo vendemos hamburguesas... vendemos momentos, sonrisas y recuerdos.
          </p>
        </div>
      </div>
    </div>

    <!-- Misión y Visión -->
    <div class="section mis-vision">
      <div class="container">
        <h2 class="title">Nuestra Misión & Visión</h2>
        <div class="grid-mis-vision">
          <div class="card fade-in-up">
            <div class="icon">🎯</div>
            <h3>Misión</h3>
            <p>
              Ofrecer alimentos deliciosos y de alta calidad, preparados con ingredientes frescos y servidos con calidez salvadoreña, para crear experiencias memorables en cada visita.
            </p>
          </div>
          <div class="card fade-in-up delay-1">
            <div class="icon">🚀</div>
            <h3>Visión</h3>
            <p>
              Ser la cadena de hamburguesas más querida en El Salvador, reconocida por su sabor, innovación y compromiso con la comunidad, expandiéndonos con integridad y pasión.
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Valores -->
    <div class="section valores">
      <div class="container">
        <h2 class="title">Nuestros Valores</h2>
        <div class="grid-valores">
          <div class="valor-card fade-in-up">
            <div class="icon">✨</div>
            <h3>Calidad</h3>
            <p>Ingredientes frescos, seleccionados con cuidado para cada plato.</p>
          </div>
          <div class="valor-card fade-in-up delay-1">
            <div class="icon">🔥</div>
            <h3>Sabor</h3>
            <p>Recetas únicas que resaltan el sabor salvadoreño en cada bocado.</p>
          </div>
          <div class="valor-card fade-in-up delay-2">
            <div class="icon">❤️</div>
            <h3>Servicio</h3>
            <p>Atención rápida, amable y con una sonrisa sincera.</p>
          </div>
        </div>
      </div>
    </div>

    <!-- CTA Final -->
    <div class="cta-final">
      <div class="cta-box">
        <h3>¿Listo para probar lo mejor?</h3>
        <p>Visítanos o pide a domicilio.</p>
        <router-link to="/menu" class="btn primary large">Ver Menú</router-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutView',
  mounted() {
    // Activar animaciones al montar
    document.querySelectorAll('.fade-in-up').forEach(el => {
      el.classList.add('animate');
    });
  }
}
</script>

<style scoped>
:root {
  --bg: #aeff00;
  --accent: #ff5a5f;
  --accent-2: #ffb86b;
  --muted: #9aa4b2;
  --card: #c8ff00;
  --dark: #000030;
  --darker: #0a0720;
}

.charlie-about {
  font-family: 'Montserrat', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  color: #e6eef6;
  background: linear-gradient(180deg, var(--darker) 0%, var(--dark) 60%);
  padding-bottom: 40px;
  overflow-x: hidden;
}

/* HERO con Logo Pequeño y Estético */
.hero {
  padding: 60px 20px 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.hero::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 90, 95, 0.3), transparent);
}

.hero-content {
  display: flex;
  align-items: center;
  gap: 30px;
  max-width: 1000px;
  width: 100%;
}

.logo-wrapper {
  flex-shrink: 0;
  width: 180px;
  height: 180px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 16px;
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.03), rgba(255, 255, 255, 0.01));
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
  overflow: hidden;
  transition: transform 0.3s ease;
}

.logo-wrapper:hover {
  transform: scale(1.05);
}

.logo {
  width: 100%;
  height: auto;
  object-fit: contain;
  border-radius: 12px;
  filter: drop-shadow(0 4px 10px rgba(0, 0, 0, 0.3));
}

.text-content {
  flex: 1;
  min-width: 0;
}

.brand {
  font-size: 2.5rem;
  letter-spacing: -1px;
  margin: 0 0 12px;
  color: white;
  text-shadow: 0 4px 20px rgba(0, 0, 0, 0.6);
  line-height: 1.2;
}

.tag {
  color: var(--accent-2);
  font-weight: 600;
  margin-bottom: 16px;
  font-size: 1.1rem;
  opacity: 0.9;
}

.hero-ctas {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 10px;
}

.btn {
  background: transparent;
  border: 0;
  padding: 10px 20px;
  border-radius: 999px;
  cursor: pointer;
  font-weight: 700;
  transition: all 0.2s ease;
  font-size: 0.95rem;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.btn.primary {
  background: linear-gradient(90deg, var(--accent), #ff7a59);
  color: #091019;
  box-shadow: 0 6px 20px rgba(255, 90, 95, 0.2);
}
.btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 30px rgba(255, 90, 95, 0.3);
}

.btn.outline {
  border: 1px solid rgba(255, 255, 255, 0.12);
  color: white;
  background: rgba(255, 255, 255, 0.02);
}
.btn.outline:hover {
  background: rgba(255, 255, 255, 0.05);
  transform: translateY(-2px);
}

/* HISTORIA */
.historia {
  padding: 40px 20px;
  position: relative;
}

.historia::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 184, 107, 0.2), transparent);
}

.title {
  font-size: 2.2rem;
  color: white;
  margin-bottom: 16px;
  text-align: center;
  letter-spacing: -0.5px;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.4);
}

.history-text {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
  font-size: 1rem;
  line-height: 1.6;
  color: var(--muted);
}

.history-text p {
  margin: 12px 0;
}

.history-text p strong {
  color: white;
  font-weight: 700;
}

.motto {
  color: var(--accent-2);
  font-style: italic;
  font-weight: 700;
  margin-top: 16px;
  font-size: 1.05rem;
}

/* MISIÓN & VISIÓN */
.mis-vision {
  padding: 40px 20px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.01), rgba(255, 255, 255, 0.005));
  position: relative;
}

.mis-vision::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 184, 107, 0.2), transparent);
}

.grid-mis-vision {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  max-width: 1000px;
  margin: 0 auto;
}

.card {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
}

.icon {
  font-size: 2.2rem;
  margin-bottom: 12px;
  color: var(--accent-2);
}

.card h3 {
  color: white;
  margin: 0 0 10px;
  font-size: 1.2rem;
}

.card p {
  color: var(--muted);
  font-size: 0.9rem;
  line-height: 1.5;
}

/* VALORES */
.valores {
  padding: 40px 20px;
  position: relative;
}

.valores::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 90, 95, 0.3), transparent);
}

.grid-valores {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 20px;
  max-width: 1000px;
  margin: 0 auto;
}

.valor-card {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.valor-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
}

.valor-card .icon {
  font-size: 2.2rem;
  margin-bottom: 12px;
  color: var(--accent-2);
}

.valor-card h3 {
  color: white;
  margin: 0 0 10px;
  font-size: 1.2rem;
}

.valor-card p {
  color: var(--muted);
  font-size: 0.9rem;
  line-height: 1.5;
}

/* Fade In Up */
.fade-in-up {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.fade-in-up.animate {
  opacity: 1;
  transform: translateY(0);
}

.delay-1 {
  transition-delay: 0.15s;
}

.delay-2 {
  transition-delay: 0.3s;
}

/* CTA FINAL */
.cta-final {
  padding: 40px 20px;
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.1), rgba(0, 0, 0, 0.05));
  text-align: center;
}

.cta-box {
  max-width: 500px;
  margin: 0 auto;
  padding: 24px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
  border-radius: 14px;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
}

.cta-box h3 {
  color: white;
  font-size: 1.8rem;
  margin-bottom: 12px;
  letter-spacing: -0.5px;
}

.cta-box p {
  color: var(--muted);
  margin-bottom: 16px;
  font-size: 1rem;
}

.btn.large {
  padding: 12px 28px;
  font-size: 1.05rem;
}

/* RESPONSIVE */
@media (max-width: 900px) {
  .hero {
    padding: 40px 20px 20px;
    flex-direction: column;
    text-align: center;
  }
  .hero-content {
    flex-direction: column;
    gap: 20px;
  }
  .logo-wrapper {
    width: 150px;
    height: 150px;
  }
  .brand {
    font-size: 2.2rem;
  }
  .title {
    font-size: 2rem;
  }
  .cta-box {
    padding: 20px;
  }
}
</style>