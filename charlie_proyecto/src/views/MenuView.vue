<template>
  <div class="charlie-home">
    <div class="menu-container">
      <!-- Header del Menú con animación -->
      <div class="menu-header">
        <div class="header-decoration"></div>
        <h1 class="menu-title">Nuestro Menú</h1>
        <p class="menu-subtitle">Pizzas especiales con ingredientes únicos</p>
        <div class="header-ornament">
          <span class="ornament-dot"></span>
          <span class="ornament-line"></span>
          <span class="ornament-dot"></span>
        </div>
      </div>
      <!-- Filtros/Categorías con tabs -->
      <div class="category-tabs">
        <button 
          v-for="cat in categories" 
          :key="cat.id"
          :class="['tab-btn', { active: activeCategory === cat.id }]"
          @click="activeCategory = cat.id"
        >
          <span class="tab-icon">{{ cat.icon }}</span>
          <span class="tab-label">{{ cat.label }}</span>
        </button>
      </div>
      <!-- Sección de Pizzas -->
      <section v-show="activeCategory === 'pizzas'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">01</span>
            <h2 class="section-title">Pizzas Especiales</h2>
          </div>
          <div class="price-legend">
            <div class="legend-item">
              <span class="legend-icon">🍕</span>
              <span class="size-label">Personal</span>
            </div>
            <div class="legend-item">
              <span class="legend-icon">🍕</span>
              <span class="size-label">Grande</span>
            </div>
          </div>
        </div>
        <div class="menu-grid">
          <!-- Pizza de un ingrediente especial -->
          <div class="menu-item">
            <div class="item-badge">Personalizable</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Pizza de un ingrediente especial</h3>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$12.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Chicken Alfredo -->
          <div class="menu-item featured">
            <div class="item-badge popular">Popular</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Chicken Alfredo</h3>
                <p class="item-description">salsa Alfredo, pollo, hongos frescos</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.75</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$12.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Chicken Buffalo -->
          <div class="menu-item">
            <div class="item-badge spicy">Picante 🌶️</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Chicken Buffalo</h3>
                <p class="item-description">Pollo y salsa Buffalo</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$8.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$11.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Chicken Teriyaki y Miel -->
          <div class="menu-item">
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Chicken Teriyaki y Miel</h3>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$12.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Spicy BBQ Chicken y Piña -->
          <div class="menu-item">
            <div class="item-badge spicy">Picante 🌶️</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Spicy BBQ Chicken y Piña</h3>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$12.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Tijuana -->
          <div class="menu-item featured">
            <div class="item-badge special">Especial</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Tijuana</h3>
                <p class="item-description">Doritos, Carne Asada, lechuga</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$11.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$16.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Madrid -->
          <div class="menu-item">
            <div class="item-badge premium">Premium</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Madrid</h3>
                <p class="item-description">Jamón Serrano, aceitunas verdes</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$13.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Loroco -->
          <div class="menu-item">
            <div class="item-badge local">Local</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Loroco</h3>
                <p class="item-description">Loroco, Salsa Blanca</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$8.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$11.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Cantaloa -->
          <div class="menu-item">
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Cantaloa</h3>
                <p class="item-description">Pimientos asados y chorizo español</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$8.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$11.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Vegetariana -->
          <div class="menu-item">
            <div class="item-badge veggie">Vegetariana 🌱</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Vegetariana</h3>
                <p class="item-description">Zuccini, pimientos asados, hongos frescos, aceite de oliva</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$8.90</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$12.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Hawaiana -->
          <div class="menu-item">
            <div class="item-badge popular">Popular</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Hawaiana</h3>
                <p class="item-description">Jamón, Piña, tocino</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$14.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Barca -->
          <div class="menu-item featured">
            <div class="item-badge premium">Premium</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Barca</h3>
                <p class="item-description">Camarones, Jamón serrano y Aceite de oliva</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$11.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$16.75</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Palermo -->
          <div class="menu-item">
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Palermo</h3>
                <p class="item-description">Salamme, Aceitunas verdes</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$14.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Recoleta -->
          <div class="menu-item">
            <div class="item-badge premium">Premium</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Recoleta</h3>
                <p class="item-description">Tocino, Camarones, Hongo fresco</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$11.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$16.75</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Perla Negra -->
          <div class="menu-item featured">
            <div class="item-badge exclusive">Exclusiva</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Perla Negra</h3>
                <p class="item-description">Calamares en su tinta y camarón salteados al ajo</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$11.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$16.95</span>
                </div>
              </div>
            </div>
          </div>
          <!-- Margarita -->
          <div class="menu-item">
            <div class="item-badge classic">Clásica</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">Margarita</h3>
                <p class="item-description">Tomate y Albahaca</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$9.50</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$14.50</span>
                </div>
              </div>
            </div>
          </div>
          <!-- California -->
          <div class="menu-item featured">
            <div class="item-badge premium">Premium</div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">California</h3>
                <p class="item-description">Camarones Salteados al Ajo, Hongos Frescos y Salsa Alfredo</p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">$11.95</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">$16.95</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- Sección de Bebidas -->
      <section v-show="activeCategory === 'bebidas'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">02</span>
            <h2 class="section-title">Bebidas</h2>
          </div>
        </div>
        <div class="drinks-grid">
          <!-- Sodas -->
          <div class="drink-item">
            <div class="drink-icon">🥤</div>
            <div class="drink-info">
              <h3 class="drink-name">Sodas</h3>
              <p class="drink-description">Cocacola, Fanta, Sprite, Colashampan, Uva, Fresa, Crema Soda</p>
            </div>
            <div class="drink-price">$1.40</div>
          </div>
          <!-- Te Helado -->
          <div class="drink-item">
            <div class="drink-icon">🧊</div>
            <div class="drink-info">
              <h3 class="drink-name">Te Helado Lipton 354 ml</h3>
              <p class="drink-description">Durazno - Limón</p>
            </div>
            <div class="drink-price">$1.60</div>
          </div>
          <!-- Agua -->
          <div class="drink-item">
            <div class="drink-icon">💧</div>
            <div class="drink-info">
              <h3 class="drink-name">Agua</h3>
            </div>
            <div class="drink-price">$1.25</div>
          </div>
          <!-- Soda de 1.5 Lts -->
          <div class="drink-item featured">
            <div class="drink-icon">🥤</div>
            <div class="drink-info">
              <h3 class="drink-name">Soda de 1.5 Lts</h3>
              <span class="drink-badge">Familiar</span>
            </div>
            <div class="drink-price">$3.95</div>
          </div>
          <!-- Pichel de Te -->
          <div class="drink-item featured">
            <div class="drink-icon">🍹</div>
            <div class="drink-info">
              <h3 class="drink-name">Pichel de Te, Horchata o SODA</h3>
              <span class="drink-badge">Para Compartir</span>
            </div>
            <div class="drink-price">$5.50</div>
          </div>
          <!-- Vaso de Horchata -->
          <div class="drink-item">
            <div class="drink-icon">🥛</div>
            <div class="drink-info">
              <h3 class="drink-name">Vaso de Horchata 16 onz</h3>
            </div>
            <div class="drink-price">$1.50</div>
          </div>
          <!-- Limonada o Naranjada -->
          <div class="drink-item">
            <div class="drink-icon">🍋</div>
            <div class="drink-info">
              <h3 class="drink-name">Limonada o Naranjada</h3>
              <span class="drink-badge fresh">Fresca</span>
            </div>
            <div class="drink-price">$1.50</div>
          </div>
          <!-- Jugo de Naranja -->
          <div class="drink-item">
            <div class="drink-icon">🍊</div>
            <div class="drink-info">
              <h3 class="drink-name">Jugo de Naranja</h3>
              <span class="drink-badge fresh">Natural</span>
            </div>
            <div class="drink-price">$1.50</div>
          </div>
          <!-- Limonada o Naranjada c/Soda -->
          <div class="drink-item">
            <div class="drink-icon">✨</div>
            <div class="drink-info">
              <h3 class="drink-name">Limonada o Naranjada c/Soda</h3>
              <span class="drink-badge">Gasificada</span>
            </div>
            <div class="drink-price">$2.50</div>
          </div>
        </div>
      </section>
      <!-- Sección de Shakes -->
      <section v-show="activeCategory === 'shakes'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">03</span>
            <h2 class="section-title">Shakes</h2>
          </div>
        </div>
        <div class="shakes-grid">
          <!-- Nutella Milk Shake -->
          <div class="shake-card">
            <div class="shake-header">
              <span class="shake-icon">🍫</span>
              <h3 class="shake-name">Nutella Milk Shake</h3>
            </div>
            <div class="shake-footer">
              <span class="shake-price">$2.95</span>
            </div>
          </div>
          <!-- Nutella Oreo Milk Shake -->
          <div class="shake-card premium">
            <div class="shake-badge">Especial</div>
            <div class="shake-header">
              <span class="shake-icon">🍪</span>
              <h3 class="shake-name">Nutella Oreo Milk Shake</h3>
            </div>
            <div class="shake-footer">
              <span class="shake-price">$3.50</span>
            </div>
          </div>
          <!-- Strawberry Milk Shake -->
          <div class="shake-card">
            <div class="shake-header">
              <span class="shake-icon">🍓</span>
              <h3 class="shake-name">Strawberry Milk Shake</h3>
            </div>
            <div class="shake-footer">
              <span class="shake-price">$2.95</span>
            </div>
          </div>
          <!-- Tropical Passion -->
          <div class="shake-card tropical">
            <div class="shake-badge tropical">Tropical</div>
            <div class="shake-header">
              <span class="shake-icon">🥭</span>
              <h3 class="shake-name">Tropical Passion</h3>
              <p class="shake-desc">Vainilla, Maracuya</p>
            </div>
            <div class="shake-footer">
              <span class="shake-price">$3.50</span>
            </div>
          </div>
          <!-- Citrus Berrylicious -->
          <div class="shake-card fresh">
            <div class="shake-badge fresh">Refrescante</div>
            <div class="shake-header">
              <span class="shake-icon">🍋</span>
              <h3 class="shake-name">Citrus Berrylicious</h3>
            </div>
            <div class="shake-footer">
              <span class="shake-price">$3.50</span>
            </div>
          </div>
        </div>
      </section>
      <!-- Sección de Hot Dogs -->
      <section v-show="activeCategory === 'hotdogs'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">04</span>
            <h2 class="section-title">Hot Dogs</h2>
          </div>
        </div>
        <div class="hotdogs-grid">
          <!-- Mega Hot-Dog -->
          <div class="hotdog-item">
            <div class="hotdog-icon">🌭</div>
            <div class="hotdog-info">
              <h3 class="hotdog-name">Mega Hot-Dog</h3>
            </div>
            <div class="hotdog-price">$2.75</div>
          </div>
          <!-- Tex Mex Dog -->
          <div class="hotdog-item">
            <div class="hotdog-icon">🌶️</div>
            <div class="hotdog-info">
              <h3 class="hotdog-name">Tex Mex Dog</h3>
              <p class="hotdog-description">(Salsa de queso Cheddar y jalapeños)</p>
            </div>
            <div class="hotdog-price">$3.25</div>
          </div>
          <!-- Dog Bacon Bawer -->
          <div class="hotdog-item">
            <div class="hotdog-icon">🥓</div>
            <div class="hotdog-info">
              <h3 class="hotdog-name">Dog Bacon Bawer</h3>
              <p class="hotdog-description">(Con nuestra deliciosa salsa blanca con tocino)</p>
            </div>
            <div class="hotdog-price">$3.50</div>
          </div>
          <!-- Jalapeño Hawaiian -->
          <div class="hotdog-item">
            <div class="hotdog-icon">🍍</div>
            <div class="hotdog-info">
              <h3 class="hotdog-name">Jalapeño Hawaiian</h3>
              <p class="hotdog-description">(Piña en trozos y Jalapeños)</p>
            </div>
            <div class="hotdog-price">$3.25</div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>
<script>
export default {
  name: 'MenuView',
  data() {
    return {
      activeCategory: 'pizzas',
      categories: [
        { id: 'pizzas', label: 'Pizzas', icon: '🍕' },
        { id: 'bebidas', label: 'Bebidas', icon: '🥤' },
        { id: 'shakes', label: 'Shakes', icon: '🥤' },
        { id: 'hotdogs', label: 'Hot Dogs', icon: '🌭' } // Nueva categoría añadida
      ]
    }
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
}
.charlie-home {
  font-family: 'Montserrat', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  color: #e6eef6;
  background: linear-gradient(180deg, #110b3b 0%, #000030 60%);
  min-height: 100vh;
  padding: 40px 20px 80px;
}
.menu-container {
  max-width: 1400px;
  margin: 0 auto;
}
/* ============================================
   HEADER DEL MENÚ CON DECORACIÓN
   ============================================ */
.menu-header {
  text-align: center;
  margin-bottom: 60px;
  padding: 60px 20px 40px;
  position: relative;
}
.header-decoration {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 200px;
  height: 4px;
  background: linear-gradient(90deg, transparent, var(--accent), var(--accent-2), transparent);
  border-radius: 2px;
  box-shadow: 0 0 20px rgba(255, 90, 95, 0.5);
}
.menu-title {
  font-size: 3.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-2) 50%, #ffd700 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 16px;
  letter-spacing: -2px;
  text-transform: uppercase;
  position: relative;
  display: inline-block;
}
.menu-subtitle {
  font-size: 1.2rem;
  color: var(--muted);
  font-weight: 300;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 30px;
}
.header-ornament {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  margin-top: 30px;
}
.ornament-dot {
  width: 8px;
  height: 8px;
  background: var(--accent-2);
  border-radius: 50%;
  box-shadow: 0 0 10px var(--accent-2);
}
.ornament-line {
  width: 100px;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--accent-2), transparent);
}
/* ============================================
   TABS DE CATEGORÍAS
   ============================================ */
.category-tabs {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-bottom: 50px;
  flex-wrap: wrap;
}
.tab-btn {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 16px 32px;
  background: rgba(255, 255, 255, 0.03);
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: 50px;
  color: #e6eef6;
  font-size: 1.05rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}
.tab-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 90, 95, 0.2), transparent);
  transition: left 0.5s;
}
.tab-btn:hover::before {
  left: 100%;
}
.tab-btn:hover {
  border-color: var(--accent);
  background: rgba(255, 90, 95, 0.1);
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(255, 90, 95, 0.3);
}
.tab-btn.active {
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  border-color: var(--accent-2);
  color: #fff;
  box-shadow: 0 8px 25px rgba(255, 90, 95, 0.4);
  transform: translateY(-3px);
}
.tab-icon {
  font-size: 1.4rem;
  filter: grayscale(0.5);
  transition: filter 0.3s;
}
.tab-btn.active .tab-icon {
  filter: grayscale(0);
}
.tab-label {
  text-transform: uppercase;
  letter-spacing: 1px;
}
/* ============================================
   SECCIÓN DEL MENÚ
   ============================================ */
.menu-section {
  margin-bottom: 80px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.03));
  border-radius: 30px;
  padding: 50px 40px;
  box-shadow: 
    0 20px 60px rgba(0, 0, 0, 0.4),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  position: relative;
  border: 1px solid rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
}
.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 40px;
  padding-bottom: 25px;
  border-bottom: 2px solid rgba(255,90, 95, 0.2);
  position: relative;
}
.section-header::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 150px;
  height: 2px;
  background: linear-gradient(90deg, var(--accent), var(--accent-2));
  box-shadow: 0 0 10px var(--accent);
}
.section-title-wrapper {
  display: flex;
  align-items: center;
  gap: 20px;
}
.section-number {
  font-size: 3rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  opacity: 0.3;
  line-height: 1;
}
.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #fff;
  letter-spacing: -1px;
  position: relative;
}
.price-legend {
  display: flex;
  gap: 30px;
}
.legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.1);
}
.legend-icon {
  font-size: 1.2rem;
}
.size-label {
  font-size: 0.85rem;
  color: var(--accent-2);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1px;
}
/* ============================================
   GRID DE PIZZAS - DISEÑO DE TARJETAS
   ============================================ */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
  gap: 25px;
}
.menu-item {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.03), rgba(255, 255, 255, 0.01));
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  position: relative;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}
.menu-item::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 90, 95, 0.05), transparent);
  transition: left 0.6s;
}
.menu-item:hover::before {
  left: 100%;
}
.menu-item:hover {
  border-color: var(--accent);
  box-shadow: 
    0 15px 40px rgba(255, 90, 95, 0.2),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  transform: translateY(-5px);
}
.menu-item.featured {
  border-color: rgba(255, 184, 107, 0.3);
  background: linear-gradient(135deg, rgba(255, 184, 107, 0.05), rgba(255, 90, 95, 0.03));
}
.menu-item.featured:hover {
  border-color: var(--accent-2);
  box-shadow: 
    0 15px 40px rgba(255, 184, 107, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
}
/* BADGES ESTILIZADOS */
.item-badge {
  position: absolute;
  top: 15px;
  right: 15px;
  padding: 6px 16px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #fff;
  backdrop-filter: blur(10px);
  z-index: 2;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}
.item-badge.popular {
  background: linear-gradient(135deg, #ff6b6b, #ee5a6f);
  border-color: #ff8787;
  animation: pulse 2s ease-in-out infinite;
}
.item-badge.spicy {
  background: linear-gradient(135deg, #ff4500, #ff6347);
  border-color: #ff6347;
}
.item-badge.special {
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  border-color: var(--accent-2);
}
.item-badge.premium {
  background: linear-gradient(135deg, #ffd700, #ffed4e);
  border-color: #ffd700;
  color: #000;
}
.item-badge.local {
  background: linear-gradient(135deg, #00b894, #00cec9);
  border-color: #00cec9;
}
.item-badge.veggie {
  background: linear-gradient(135deg, #55efc4, #00b894);
  border-color: #55efc4;
}
.item-badge.exclusive {
  background: linear-gradient(135deg, #6c5ce7, #a29bfe);
  border-color: #a29bfe;
}
.item-badge.classic {
  background: linear-gradient(135deg, #636e72, #b2bec3);
  border-color: #b2bec3;
}
@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.05); }
}
/* CONTENIDO DE LA TARJETA */
.item-content {
  padding: 25px;
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.item-info {
  flex: 1;
}
.item-name {
  font-size: 1.3rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 10px;
  letter-spacing: -0.5px;
  line-height: 1.3;
}
.item-description {
  font-size: 0.95rem;
  color: var(--muted);
  line-height: 1.6;
  font-weight: 300;
  margin-bottom: 15px;
}
.item-divider {
  width: 50px;
  height: 3px;
  background: linear-gradient(90deg, var(--accent), transparent);
  border-radius: 2px;
  margin-top: 12px;
}
/* PRECIOS EN FORMATO BOX */
.item-prices {
  display: flex;
  gap: 15px;
  justify-content: flex-start;
}
.price-box {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 12px;
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 12px;
  transition: all 0.3s ease;
}
.price-box:hover {
  background: rgba(255, 90, 95, 0.1);
  border-color: var(--accent);
  transform: scale(1.05);
}
.price-label {
  font-size: 0.7rem;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: 600;
  margin-bottom: 5px;
}
.price {
  font-size: 1.4rem;
  font-weight: 800;
  color: var(--accent-2);
  text-shadow: 0 0 15px rgba(255, 184, 107, 0.4);
  font-family: 'Courier New', monospace;
}
.price.highlight {
  color: var(--accent);
  text-shadow: 0 0 15px rgba(255, 90, 95, 0.5);
  font-size: 1.6rem;
}
/* ============================================
   BEBIDAS - DISEÑO HORIZONTAL
   ============================================ */
.drinks-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(450px, 1fr));
  gap: 20px;
}
.drink-item {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 20px 25px;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0.03), rgba(255, 255, 255, 0.01));
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}
.drink-item::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, var(--accent), var(--accent-2));
  transform: scaleY(0);
  transition: transform 0.3s ease;
}
.drink-item:hover::before {
  transform: scaleY(1);
}
.drink-item:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: var(--accent);
  transform: translateX(5px);
  box-shadow: 0 8px 25px rgba(255, 90, 95, 0.15);
}
.drink-item.featured {
  border-color: rgba(255, 184, 107, 0.3);
  background: linear-gradient(90deg, rgba(255, 184, 107, 0.05), transparent);
}
.drink-icon {
  font-size: 2.5rem;
  flex-shrink: 0;
  filter: drop-shadow(0 0 10px rgba(255, 184, 107, 0.3));
}
.drink-info {
  flex: 1;
}
.drink-name {
  font-size: 1.1rem;
  font-weight: 600;
  color: #ffffff;
  margin-bottom: 5px;
  letter-spacing: -0.3px;
}
.drink-description {
  font-size: 0.85rem;
  color: var(--muted);
  line-height: 1.4;
  font-weight: 300;
}
.drink-badge {
  display: inline-block;
  padding: 4px 12px;
  background: rgba(255, 184, 107, 0.2);
  border: 1px solid var(--accent-2);
  border-radius: 12px;
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  color: var(--accent-2);
  margin-top: 6px;
}
.drink-badge.fresh {
  background: rgba(0, 184, 148, 0.2);
  border-color: #00b894;
  color: #00b894;
}
.drink-price {
  font-size: 1.5rem;
  font-weight: 800;
  color: var(--accent);
  flex-shrink: 0;
  min-width: 80px;
  text-align: right;
  text-shadow: 0 0 15px rgba(255, 90, 95, 0.4);
  font-family: 'Courier New', monospace;
}
/* ============================================
   SHAKES - DISEÑO DE TARJETAS VISUALES
   ============================================ */
.shakes-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 25px;
}
.shake-card {
  background: linear-gradient(135deg, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0.02));
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 30px;
  position: relative;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 200px;
}
.shake-card::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255, 90, 95, 0.1) 0%, transparent 70%);
  transition: transform 0.6s ease;
  transform: scale(0);
}
.shake-card:hover::before {
  transform: scale(1);
}
.shake-card:hover {
  border-color: var(--accent);
  box-shadow: 
    0 20px 50px rgba(255, 90, 95, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  transform: translateY(-8px) scale(1.02);
}
.shake-card.premium {
  border-color: rgba(255, 215, 0, 0.3);
  background: linear-gradient(135deg, rgba(255, 215, 0, 0.05), rgba(255, 184, 107, 0.03));
}
.shake-card.premium:hover {
  border-color: #ffd700;
  box-shadow: 
    0 20px 50px rgba(255, 215, 0, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
}
.shake-card.tropical {
  border-color: rgba(255, 159, 64, 0.3);
  background: linear-gradient(135deg, rgba(255, 159, 64, 0.05), rgba(255, 206, 86, 0.03));
}
.shake-card.tropical:hover {
  border-color: #ff9f40;
  box-shadow: 0 20px 50px rgba(255, 159, 64, 0.3);
}
.shake-card.fresh {
  border-color: rgba(0, 184, 148, 0.3);
  background: linear-gradient(135deg, rgba(0, 184, 148, 0.05), rgba(85, 239, 196, 0.03));
}
.shake-card.fresh:hover {
  border-color: #00b894;
  box-shadow: 0 20px 50px rgba(0, 184, 148, 0.3);
}
.shake-badge {
  position: absolute;
  top: 15px;
  right: 15px;
  padding: 6px 14px;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  border-radius: 20px;
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 1px;
  color: #fff;
  box-shadow: 0 4px 15px rgba(255, 90, 95, 0.4);
}
.shake-badge.tropical {
  background: linear-gradient(135deg, #ff9f40, #ffce56);
  color: #000;
}
.shake-badge.fresh {
  background: linear-gradient(135deg, #00b894, #55efc4);
}
.shake-header {
  text-align: center;
  margin-bottom: 20px;
}
.shake-icon {
  font-size: 3.5rem;
  display: block;
  margin-bottom: 15px;
  filter: drop-shadow(0 4px 10px rgba(255, 184, 107, 0.3));
  animation: float 3s ease-in-out infinite;
}
@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}
.shake-name {
  font-size: 1.2rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  letter-spacing: -0.3px;
}
.shake-desc {
  font-size: 0.85rem;
  color: var(--muted);
  margin-top: 8px;
  font-weight: 300;
}
.shake-footer {
  display: flex;
  justify-content: center;
  align-items: center;
  padding-top: 20px;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  margin-top: auto;
}
.shake-price {
  font-size: 2rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-family: 'Courier New', monospace;
  text-shadow: 0 0 20px rgba(255, 90, 95, 0.5);
}
/* ============================================
   HOT DOGS - DISEÑO HORIZONTAL (similar a Bebidas)
   ============================================ */
.hotdogs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(450px, 1fr));
  gap: 20px;
}
.hotdog-item {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 20px 25px;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0.03), rgba(255, 255, 255, 0.01));
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}
.hotdog-item::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 4px;
  height: 100%;
  background: linear-gradient(180deg, var(--accent), var(--accent-2));
  transform: scaleY(0);
  transition: transform 0.3s ease;
}
.hotdog-item:hover::before {
  transform: scaleY(1);
}
.hotdog-item:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: var(--accent);
  transform: translateX(5px);
  box-shadow: 0 8px 25px rgba(255, 90, 95, 0.15);
}
.hotdog-icon {
  font-size: 2.5rem;
  flex-shrink: 0;
  filter: drop-shadow(0 0 10px rgba(255, 184, 107, 0.3));
}
.hotdog-info {
  flex: 1;
}
.hotdog-name {
  font-size: 1.1rem;
  font-weight: 600;
  color: #ffffff;
  margin-bottom: 5px;
  letter-spacing: -0.3px;
}
.hotdog-description {
  font-size: 0.85rem;
  color: var(--muted);
  line-height: 1.4;
  font-weight: 300;
}
.hotdog-price {
  font-size: 1.5rem;
  font-weight: 800;
  color: var(--accent);
  flex-shrink: 0;
  min-width: 80px;
  text-align: right;
  text-shadow: 0 0 15px rgba(255, 90, 95, 0.4);
  font-family: 'Courier New', monospace;
}
/* ============================================
   RESPONSIVE DESIGN
   ============================================ */
@media (max-width: 1024px) {
  .menu-grid {
    grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  }
  .drinks-grid {
    grid-template-columns: 1fr;
  }
  .hotdogs-grid {
    grid-template-columns: 1fr;
  }
}
@media (max-width: 768px) {
  .menu-title {
    font-size: 2.5rem;
  }
  .menu-subtitle {
    font-size: 1rem;
  }
  .category-tabs {
    gap: 12px;
  }
  .tab-btn {
    padding: 12px 24px;
    font-size: 0.95rem;
  }
  .section-title {
    font-size: 1.8rem;
  }
  .section-number {
    font-size: 2rem;
  }
  .section-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 20px;
  }
  .price-legend {
    width: 100%;
    justify-content: space-between;
  }
  .menu-grid {
    grid-template-columns: 1fr;
  }
  .shakes-grid {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  }
  .menu-section {
    padding: 35px 25px;
  }
}
@media (max-width: 480px) {
  .charlie-home {
    padding: 20px 10px 60px;
  }
  .menu-header {
    padding: 40px 15px 30px;
  }
  .menu-title {
    font-size: 2rem;
  }
  .menu-subtitle {
    font-size: 0.9rem;
  }
  .tab-btn {
    padding: 10px 20px;
    font-size: 0.9rem;
    gap: 8px;
  }
  .tab-icon {
    font-size: 1.2rem;
  }
  .section-title {
    font-size: 1.5rem;
  }
  .section-number {
    font-size: 1.5rem;
  }
  .item-name {
    font-size: 1.1rem;
  }
  .item-description {
    font-size: 0.85rem;
  }
  .price {
    font-size: 1.2rem;
  }
  .price.highlight {
    font-size: 1.4rem;
  }
  .drink-icon {
    font-size: 2rem;
  }
  .drink-name {
    font-size: 1rem;
  }
  .drink-price {
    font-size: 1.3rem;
  }
  .shake-icon {
    font-size: 2.5rem;
  }
  .shake-name {
    font-size: 1.05rem;
  }
  .shake-price {
    font-size: 1.6rem;
  }
  .shakes-grid {
    grid-template-columns: 1fr;
  }
  .menu-section {
    padding: 25px 20px;
  }
  .hotdog-icon {
    font-size: 2rem;
  }
  .hotdog-name {
    font-size: 1rem;
  }
  .hotdog-price {
    font-size: 1.3rem;
  }
}
</style>