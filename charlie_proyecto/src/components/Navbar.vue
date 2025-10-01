<template>
  <nav class="navbar">
    <div class="nav-left">
      <ul>
        <li><router-link to="/">Inicio</router-link></li>
        <li><router-link to="/menu">Menú</router-link></li>
        <li><router-link to="/delivery">Delivery</router-link></li>
        <li><router-link to="/about">Sobre Nosotros</router-link></li>
        <li><router-link to="/contact">Ubicación & Contacto</router-link></li>
        <li><router-link to="/promotions">Promociones</router-link></li>
        <li><router-link to="/reviews">Reseñas</router-link></li>
      </ul>
    </div>
    <div class="nav-right">
      <router-link to="/login" class="login-btn">Login</router-link>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  background: #ff6600;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.nav-left ul {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  margin: 0;
  padding: 0;
}

.nav-left a {
  color: white;
  text-decoration: none;
  font-weight: bold;
  transition: color 0.2s ease;
  position: relative;
}

.nav-left a:hover {
  color: #222;
}

.nav-left a.router-link-active {
  border-bottom: 2px solid white;
}

/* Estilo del botón elegante */
.login-btn {
  background: linear-gradient(135deg, #4a00e0, #8e2de2);
  color: white;
  padding: 0.7rem 1.4rem;
  border-radius: 999px;
  text-decoration: none;
  font-weight: bold;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(142, 45, 226, 0.3);
}

.login-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: 0.5s;
}

.login-btn:hover::before {
  left: 100%;
}

.login-btn:hover {
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 6px 20px rgba(142, 45, 226, 0.5);
  background: linear-gradient(135deg, #8e2de2, #4a00e0);
}

.login-btn:active {
  transform: translateY(-1px) scale(1.02);
}
</style>