<template>
  <div class="charlie-home">
    <!-- HERO (sin menú ni footer) -->
    <section class="hero">
      <div class="hero-inner">
        <div class="hero-text">
          <h1 class="brand">Charlie Boys</h1>
          <p class="tag">Sabores con personalidad — experiencia gastronómica &amp; buen rollo</p>
          <div class="hero-ctas">
            <button class="btn primary" @click.prevent="scrollTo('platos')">Ver platos</button>
            <button class="btn ghost" @click.prevent="scrollTo('contacto')">Reservar mesa</button>
          </div>
        </div>
        <div class="hero-art">
          <div class="plate-card">
            <img :src="featured[0].img" :alt="featured[0].title"/>
            <div class="plate-info">
              <h3>{{ featured[0].title }}</h3>
              <p class="desc">{{ featured[0].desc }}</p>
              <div class="meta">{{ featured[0].price }}</div>
            </div>
          </div>
          <div class="floating-badges">
            <div class="badge">Delivery</div>
            <div class="badge">Cocina casera</div>
            <div class="badge">Ingredientes locales</div>
          </div>
        </div>
      </div>
    </section>

    <!-- CARDS DE SERVICIOS / VALORES -->
    <section class="values">
      <div class="container">
        <div class="value-card" v-for="(v, i) in values" :key="i">
          <div class="ico" v-html="v.icon"></div>
          <h4>{{ v.title }}</h4>
          <p>{{ v.text }}</p>
        </div>
      </div>
    </section>

    <!-- PLATOS DESTACADOS (cards) -->
    <section id="platos" class="platos">
      <h2 class="section-title">Platos destacados</h2>
      <div class="grid-cards">
        <article class="card" v-for="(p, i) in platos" :key="i">
          <div class="card-media">
            <img :src="p.img" :alt="p.title"/>
            <div class="price">{{ p.price }}</div>
          </div>
          <div class="card-body">
            <h3>{{ p.title }}</h3>
            <p class="small">{{ p.desc }}</p>
            <div class="card-actions">
              <button class="btn small" @click.prevent="addToCart(p)">Agregar</button>
              <button class="btn outline small" @click.prevent="openQuickView(p)">Ver</button>
            </div>
          </div>
        </article>
      </div>
    </section>

    <!-- BLOQUE ESPECIAL / PROMO -->
    <section class="special">
      <div class="special-inner">
        <div class="special-text">
          <h2>Combo Charlie: 2x1 los miércoles</h2>
          <p>Combina una hamburguesa Charlie con papas rústicas y bebida por un precio especial. Solo los miércoles — reserva con anticipación.</p>
          <div class="special-cta">
            <button class="btn primary" @click.prevent="scrollTo('platos')">Aprovechar oferta</button>
          </div>
        </div>
        <div class="special-art">
          <img :src="special.img" :alt="special.title"/>
        </div>
      </div>
    </section>

    <!-- TESTIMONIOS -->
    <section class="testimonials">
      <h2 class="section-title">Lo que dicen nuestros clientes</h2>
      <div class="test-grid">
        <div class="test-card" v-for="(t, i) in testimonials" :key="i">
          <p class="quote">"{{ t.quote }}"</p>
          <div class="by">— {{ t.name }}, <span class="meta-small">{{ t.when }}</span></div>
        </div>
      </div>
    </section>

    <!-- CONTACT / NEWSLETTER SIMBÓLICA -->
    <section id="contacto" class="contact">
      <div class="contact-inner">
        <div class="contact-form">
          <h3>Reservaciones &amp; pedidos</h3>
          <p>Déjanos tu e‑mail y te contactamos para reservar o concretar un pedido.</p>
          <form @submit.prevent="subscribe">
            <input type="email" v-model="email" placeholder="tu@email.com" required />
            <button class="btn primary" type="submit">Enviar</button>
          </form>
          <p v-if="subscribed" class="success">¡Gracias! Te escribiremos en breve.</p>
        </div>
        <div class="contact-art">
          <div class="map-sim">
  <iframe
    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3876.6898268079444!2d-89.2712315!3d13.676615100000001!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8f632e4c10ffa58d%3A0x58d9c8dddf7f62b9!2sCharlie%20Boy%20Pizza%20%26%20Grill%20%E2%80%A2%20Santa%20Tecla!5e0!3m2!1ses-419!2ssv!4v1759286498130!5m2!1ses-419!2ssv"
    width="100%"
    height="100%"
    style="border:0;"
    allowfullscreen=""
    loading="lazy"
    referrerpolicy="no-referrer-when-downgrade"
  ></iframe>
</div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'HomeViewCharlie',
  data() {
    return {
      email: '',
      subscribed: false,
      featured: [
        {
          title: 'Hamburguesa Charlie',
          desc: 'Pan artesanal, carne 180g, queso ahumado y nuestra salsa secreta.',
          price: '$7.50',
          img: require('@/assets/hamburguesa-charlie.png')
        }
      ],
      values: [
        { title: 'Calidad local', text: 'Proveedores locales y productos de temporada.', icon: '<svg width="36" height="36" viewBox="0 0 24 24" fill="none"><path d="M12 2L15 8L22 9L17 14L18 21L12 18L6 21L7 14L2 9L9 8L12 2Z" stroke="currentColor" stroke-width="1.2"/></svg>' },
        { title: 'Servicio cálido', text: 'Trato humano y cercano en cada visita.', icon: '<svg width="36" height="36" viewBox="0 0 24 24" fill="none"><path d="M12 21C12 21 5 16 5 11C5 8.23858 7.23858 6 10 6C11.6569 6 13 7.34315 13 9C13 7.34315 14.3431 6 16 6C18.7614 6 21 8.23858 21 11C21 16 14 21 14 21H12Z" stroke="currentColor" stroke-width="1.2"/></svg>' },
        { title: 'Entrega rápida', text: 'Logística ágil y empaques eco‑friendly.', icon: '<svg width="36" height="36" viewBox="0 0 24 24" fill="none"><rect x="1" y="3" width="15" height="13" rx="2" stroke="currentColor" stroke-width="1.2"/><path d="M23 13V8H19V13" stroke="currentColor" stroke-width="1.2"/><path d="M5 21H6" stroke="currentColor" stroke-width="1.2"/><path d="M14 21H15" stroke="currentColor" stroke-width="1.2"/></svg>' }
      ],
      platos: [
        { title: 'Charlie Clásica', desc: 'Carne, queso, lechuga, tomate y nuestra salsa.', price: '$6.90', img: require('@/assets/hamburguesa-charlie.png') },
        { title: 'Pizza Rustica', desc: 'Masa madre, mozzarella, tomate asado y albahaca.', price: '$9.20', img: require('@/assets/pizza-rustica.png') },
        { title: 'Brownie Artesano', desc: 'Chocolate intenso, nueces y helado casero.', price: '$4.50', img: require('@/assets/brownie.png') }
      ],
      special: { title: 'Combo Charlie', img: require('@/assets/combo-charlie.png') },
      testimonials: [
        { name: 'María G.', quote: 'La mejor hamburguesa de la ciudad. Servido con cariño.', when: 'Hace 2 semanas' },
        { name: 'Roberto L.', quote: 'Ambiente genial y sabores refrescantes.', when: 'Hace 1 mes' },
        { name: 'Inés P.', quote: 'Delivery rápido y el empaque llegó perfecto.', when: 'Hace 3 días' }
      ]
    }
  },
  methods: {
    addToCart(p) { alert(`Agregaste ${p.title} al carrito (demo)`); },
    openQuickView(p) { alert(`${p.title}\n\n${p.desc}\nPrecio: ${p.price}`); },
    subscribe() { if (!this.email) return; this.subscribed = true; setTimeout(() => { this.email = ''; }, 1200); },
    scrollTo(id) { const el = document.getElementById(id); if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' }); }
  }
}
</script>

<style scoped>
:root{
  --bg:#aeff00; --accent:#ff5a5f; --accent-2:#ffb86b; --muted:#9aa4b2; --card:#c8ff00;
}
.charlie-home{font-family:'Montserrat',system-ui,-apple-system,'Segoe UI',Roboto,'Helvetica Neue',Arial;color:#e6eef6;background:linear-gradient(180deg,#110b3b 0%,#000030 60%);padding-bottom:80px}

/* SEPARADORES CREATIVOS ENTRE SECCIONES */
.hero {
  padding: 64px 20px 40px;
  position: relative;
}
.hero::after {
  content: '';
  position: absolute;
  bottom: -20px;
  left: 50%;
  transform: translateX(-50%);
  width: 80%;
  height: 6px;
  border-radius: 4px;
  background: linear-gradient(90deg, #ff5a5f, #ffb86b);
  box-shadow: 0 0 10px rgba(255,184,107,0.6);
}

.values {
  padding: 36px 20px;
  background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02));
  border-radius: 16px;
  margin: 40px auto;
  box-shadow: 0 10px 40px rgba(0,0,0,0.3);
  position: relative;
}
.values::after {
  content: '';
  position: absolute;
  bottom: -16px;
  left: 50%;
  transform: translateX(-50%);
  width: 60%;
  height: 4px;
  border-radius: 2px;
  background: var(--accent-2);
  box-shadow: 0 0 8px rgba(255,184,107,0.4);
}

.platos {
  padding: 28px 20px 0;
  position: relative;
}
.platos::after {
  content: '';
  display: block;
  width: 50px;
  height: 4px;
  margin: 20px auto;
  border-radius: 2px;
  background: var(--accent);
  box-shadow: 0 0 8px rgba(255,90,95,0.4);
}

.map-sim {
  width: 100%;
  height: 100%;
  min-height: 200px; 
  border-radius: 10px;
  overflow: hidden;
}

.contact-art .map-sim {
  height: 240px; /* o la altura que quieras */
}

.special {
  padding: 34px 20px;
  background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02));
  border-radius: 14px;
  box-shadow: 0 12px 35px rgba(0,0,0,0.3);
  margin: 40px auto;
  position: relative;
}
.special::after {
  content: '';
  position: absolute;
  bottom: -12px;
  left: 50%;
  transform: translateX(-50%);
  width: 40%;
  height: 3px;
  border-radius: 2px;
  background: var(--accent-2);
  box-shadow: 0 0 6px rgba(255,184,107,0.5);
}

.testimonials {
  padding: 28px 20px;
  position: relative;
}
.testimonials::after {
  content: '';
  display: block;
  width: 60px;
  height: 4px;
  margin: 20px auto;
  border-radius: 2px;
  background: var(--accent);
  box-shadow: 0 0 6px rgba(255,90,95,0.5);
}

.contact {
  padding: 34px 20px;
  position: relative;
}
.contact::after {
  content: '';
  display: block;
  width: 50px;
  height: 4px;
  margin: 20px auto 0;
  border-radius: 2px;
  background: var(--accent-2);
  box-shadow: 0 0 6px rgba(255,184,107,0.5);
}


.hero-inner{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:1fr 420px;gap:28px;align-items:center}
.brand{font-size:48px;letter-spacing:-1px;margin:0 0 10px;color:white;text-shadow:0 6px 30px rgba(0,0,0,0.6)}
.tag{color:var(--accent-2);font-weight:600;margin-bottom:18px;font-size:18px}
.hero-ctas .btn{margin-right:12px}
.btn{background:transparent;border:0;padding:10px 16px;border-radius:999px;cursor:pointer;font-weight:700;transition:all .18s ease;}
.btn.primary{background:linear-gradient(90deg,var(--accent),#ff7a59);color:#091019;box-shadow:0 8px 30px rgba(255,90,95,0.14);}
.btn.ghost{border:1px solid rgba(255,255,255,0.12);color:#fff}
.btn.small{padding:6px 10px;font-size:14px}
.btn.outline{border:1px solid rgba(255,255,255,0.12);background:transparent}
.hero-art{position:relative}
.plate-card{background:linear-gradient(135deg,rgba(255,255,255,0.03),rgba(255,255,255,0.01));border-radius:18px;overflow:hidden;box-shadow:0 12px 40px rgba(3,8,16,0.6);transform:translateY(-10px);}
.plate-card img{width:100%;height:260px;object-fit:cover;display:block}
.plate-info{padding:14px}
.plate-info h3{margin:0 0 6px}
.plate-info .desc{color:var(--muted);font-size:14px}
.plate-info .meta{margin-top:8px;font-weight:700}
.floating-badges{display:flex;gap:8px;margin-top:12px;flex-wrap:wrap}
.badge{background:rgba(255,255,255,0.04);padding:8px 12px;border-radius:999px;font-size:13px}
.values .container{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
.value-card{background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));border-radius:14px;padding:18px;text-align:center;box-shadow:0 8px 30px rgba(2,6,12,0.6);}
.value-card .ico{margin-bottom:12px;color:var(--accent-2)}
.value-card h4{margin:0 0 6px}
.value-card p{color:var(--muted);font-size:14px}
.grid-cards{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:18px}
.card{background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));border-radius:14px;overflow:hidden;box-shadow:0 12px 35px rgba(1,6,15,0.6);display:flex;flex-direction:column;transition:transform .18s ease,box-shadow .18s ease}
.card:hover{transform:translateY(-8px);box-shadow:0 18px 60px rgba(1,6,15,0.8)}
.card-media{position:relative}
.card-media img{width:100%;height:180px;object-fit:cover}
.price{position:absolute;right:10px;top:10px;background:linear-gradient(90deg,var(--accent),#ff8d6b);color:#091019;padding:6px 10px;border-radius:8px;font-weight:800}
.card-body{padding:14px;flex:1;display:flex;flex-direction:column}
.card-body h3{margin:0 0 6px}
.small{color:var(--muted);font-size:13px}
.card-actions{margin-top:auto;display:flex;gap:8px}
.special-inner{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:1fr 420px;gap:20px;align-items:center}
.special-text h2{margin:0 0 6px}
.special-art img{width:100%;border-radius:12px;box-shadow:0 16px 50px rgba(0,0,0,0.6)}
.test-grid{max-width:1100px;margin:16px auto 0;display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
.test-card{background:linear-gradient(180deg,rgba(255,255,255,0.01),rgba(255,255,255,0.005));padding:16px;border-radius:12px;box-shadow:0 10px 30px rgba(0,0,0,0.5)}
.quote{font-style:italic;margin:0 0 8px}
.by{font-weight:700;color:var(--muted);font-size:13px}
.contact-inner{max-width:1100px;margin:0 auto;display:grid;grid-template-columns:1fr 360px;gap:20px;align-items:center}
.contact-form{background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));padding:18px;border-radius:12px}
.contact-form input{width:100%;padding:10px 12px;border-radius:8px;border:0;margin:10px 0;background:rgba(255,255,255,0.03);color:#fff}
.contact-art .map-sim{height:160px;border-radius:10px;background:linear-gradient(90deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));display:flex;align-items:center;justify-content:center;color:var(--muted)}
.success{color:#b7f5c1;margin-top:8px}

@media (max-width:900px){
  .hero-inner,.special-inner,.contact-inner{grid-template-columns:1fr}
  .hero-art,.special-art{order:-1}
  .values .container{grid-template-columns:1fr}
}
</style>


