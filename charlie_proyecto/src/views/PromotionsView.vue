<template>
  <section class="charlie-promotions">
    <!-- Hero Section -->
    <div class="hero">
      <div class="hero-content">
        <h1 class="brand">Promociones & Novedades 🎉</h1>
        <p class="tag">Ofertas especiales y novedades del restaurante</p>
        <div class="hero-ctas">
          <router-link to="/menu" class="btn primary">Ver Menú</router-link>
        </div>
      </div>
      <div class="logo-wrapper">
        <img src="@/assets/Logo charlie.png" alt="Charlie Boys - Pizza & Grill" class="logo" />
      </div>
    </div>

    <!-- Ofertas Especiales -->
    <div class="section ofertas">
      <div class="container">
        <h2 class="title">🔥 Ofertas Especiales</h2>
        <div class="grid-ofertas">
          <!-- Promo 1 -->
          <div class="offer-card fade-in-up">
            <div class="offer-image">
              <img src="@/assets/promo1.png" alt="Capresse Burger" class="promo-img" />
            </div>
            <div class="offer-header">
              <h3>Capresse Burger</h3>
              <span class="price">$5.95</span>
            </div>
            <div class="offer-body">
              <p>Carne a la parrilla de carbón, queso Mozarella, tomate y albahaca.</p>
              <p class="promo">Incluye papas y soda</p>
            </div>
          </div>

          <!-- Promo 2 -->
          <div class="offer-card fade-in-up delay-1">
            <div class="offer-image">
              <img src="@/assets/promo2.png" alt="Franz Bacon Bawer" class="promo-img" />
            </div>
            <div class="offer-header">
              <h3>Franz Bacon Bawer</h3>
              <span class="price">$5.95</span>
            </div>
            <div class="offer-body">
              <p>Carne a la parrilla gratinada con queso mozzarella, salsa blanca y tocino.</p>
              <p class="promo">Incluye papitas y soda</p>
            </div>
          </div>

          <!-- Promo 3 -->
          <div class="offer-card fade-in-up delay-2">
            <div class="offer-image">
              <img src="@/assets/promo3.png" alt="Swiss Mushroom & Bacon" class="promo-img" />
            </div>
            <div class="offer-header">
              <h3>Swiss Mushroom & Bacon</h3>
              <span class="price">$5.95</span>
            </div>
            <div class="offer-body">
              <p>Queso suizo, champiñones y tocino. ¡Un clásico con twist!</p>
              <p class="promo">Incluye papitas y soda</p>
            </div>
          </div>

          <!-- Promo 4 -->
          <div class="offer-card fade-in-up delay-3">
            <div class="offer-image">
              <img src="@/assets/promo4.png" alt="Sweet Bacon & Shrimp" class="promo-img" />
            </div>
            <div class="offer-header">
              <h3>Sweet Bacon & Shrimp</h3>
              <span class="price">$5.95</span>
            </div>
            <div class="offer-body">
              <p>Tocino caramelizado y camarones salteados al ajo.</p>
              <p class="promo">Incluye papas y soda</p>
            </div>
          </div>

          <!-- Promo 5 -->
          <div class="offer-card fade-in-up delay-4">
            <div class="offer-image">
              <img src="@/assets/promo5.png" alt="Surf & Turf" class="promo-img" />
            </div>
            <div class="offer-header">
              <h3>Surf & Turf</h3>
              <span class="price">$5.95</span>
            </div>
            <div class="offer-body">
              <p>Camarones al ajo y carne jugosa en una sola burger.</p>
              <p class="promo">Incluye papas y soda</p>
            </div>
          </div>

          <!-- Promo 6 -->
          <div class="offer-card fade-in-up delay-5">
            <div class="offer-image">
              <img src="@/assets/promo6.png" alt="Clásica & Jalapeña" class="promo-img" />
            </div>
            <div class="offer-header">
              <h3>Clásica & Jalapeña</h3>
              <span class="price">$5.95</span>
            </div>
            <div class="offer-body">
              <p>La favorita de todos: clásica o con jalapeños.</p>
              <p class="promo">Incluye papas y soda</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Novedades -->
    <div class="section novedades">
      <div class="container">
        <h2 class="title">✨ Novedades del Restaurante</h2>
        <div class="grid-novedades">
          <!-- Novedad 1 -->
          <div class="novedad-card fade-in-up">
            <div class="novedad-header">
              <h3>¡Nuevo Burger Tuesday!</h3>
              <span class="date">Septiembre 2025</span>
            </div>
            <div class="novedad-body">
              <p>Cada martes, nuevas promociones exclusivas con precios especiales. ¡No te lo pierdas!</p>
            </div>
          </div>

          <!-- Novedad 2 -->
          <div class="novedad-card fade-in-up delay-1">
            <div class="novedad-header">
              <h3>Delivery Extendido</h3>
              <span class="date">Ahora en toda la ciudad</span>
            </div>
            <div class="novedad-body">
              <p>Ya puedes pedir a domicilio desde cualquier parte de San Salvador. ¡Rápido y fresco!</p>
            </div>
          </div>

          <!-- Novedad 3 -->
          <div class="novedad-card fade-in-up delay-2">
            <div class="novedad-header">
              <h3>Nueva Sucursal</h3>
              <span class="date">Próximamente</span>
            </div>
            <div class="novedad-body">
              <p>Estamos planeando abrir una nueva sucursal. ¡Mantente al tanto de las novedades!</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- CTA Final -->
    <div class="cta-final">
      <div class="cta-box">
        <h3>¿Listo para aprovechar las ofertas?</h3>
        <p>Pide ya o visítanos en cualquiera de nuestras sucursales.</p>
        <router-link to="/menu" class="btn primary large">Ver Menú</router-link>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PromotionsView',
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

.charlie-promotions {
  font-family: 'Montserrat', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  color: #e6eef6;
  background: linear-gradient(180deg, var(--darker) 0%, var(--dark) 60%);
  padding-bottom: 40px;
  overflow-x: hidden;
}

/* HERO */
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
  flex: 1;
  min-width: 280px;
  max-width: 500px;
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

/* OFERTAS ESPECIALES */
.ofertas {
  padding: 40px 20px;
  position: relative;
}

.ofertas::before {
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

.grid-ofertas {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  max-width: 1000px;
  margin: 0 auto;
}

.offer-card {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
}

.offer-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
}

.offer-image {
  width: 100%;
  height: 180px;
  border-radius: 12px;
  overflow: hidden;
  margin-bottom: 12px;
  position: relative;
}

.promo-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.promo-img:hover {
  transform: scale(1.05);
}

.offer-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

.offer-header h3 {
  color: white;
  margin: 0;
  font-size: 1.2rem;
}

.price {
  background: linear-gradient(90deg, var(--accent), var(--accent-2));
  color: #091019;
  padding: 4px 10px;
  border-radius: 8px;
  font-weight: 700;
  font-size: 1rem;
}

.offer-body p {
  color: var(--muted);
  margin: 8px 0 0;
  font-size: 0.9rem;
  line-height: 1.5;
}

.promo {
  color: var(--accent-2);
  font-weight: 700;
  margin-top: 8px;
  font-size: 0.9rem;
}

/* NOVEDADES */
.novedades {
  padding: 40px 20px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.01), rgba(255, 255, 255, 0.005));
  position: relative;
}

.novedades::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 90, 95, 0.3), transparent);
}

.grid-novedades {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  max-width: 1000px;
  margin: 0 auto;
}

.novedad-card {
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
  border-radius: 14px;
  padding: 20px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  flex-direction: column;
}

.novedad-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
}

.novedad-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

.novedad-header h3 {
  color: white;
  margin: 0;
  font-size: 1.2rem;
}

.date {
  background: rgba(255, 255, 255, 0.1);
  color: var(--accent-2);
  padding: 4px 8px;
  border-radius: 6px;
  font-size: 0.8rem;
  font-weight: 600;
}

.novedad-body p {
  color: var(--muted);
  margin: 0;
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

.delay-3 {
  transition-delay: 0.45s;
}

.delay-4 {
  transition-delay: 0.6s;
}

.delay-5 {
  transition-delay: 0.75s;
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
    order: 1;
    max-width: 100%;
  }
  .logo-wrapper {
    order: 2;
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
  .offer-image {
    height: 160px;
  }
}
</style>