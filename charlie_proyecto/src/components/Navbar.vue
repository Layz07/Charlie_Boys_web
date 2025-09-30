<template>
  <nav class="navbar">
    <ul>
      <li><router-link to="/">Inicio</router-link></li>
      <li><router-link to="/menu">Menú</router-link></li>
      <li><router-link to="/delivery">Delivery</router-link></li>
      <li><router-link to="/about">Sobre Nosotros</router-link></li>
      <li><router-link to="/contact">Ubicación & Contacto</router-link></li>
      <li><router-link to="/promotions">Promociones</router-link></li>
      <li><router-link to="/reviews">Reseñas</router-link></li>
      <li><router-link to="/login">Login</router-link></li>
    </ul>
  </nav>
</template>

<style scoped>
.navbar {
  background: #ff6600;
  padding: 1rem;
}
ul {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  margin: 0;
  padding: 0;
}
a {
  color: white;
  text-decoration: none;
  font-weight: bold;
  transition: color 0.2s ease;
}
a:hover {
  color: #222;
}
a.router-link-active {
  border-bottom: 2px solid white;
}
</style>
