<template>
  <div id="app">
    <Navbar />
    <router-view />
    <footer class="footer">
      <p>© 2025 Charlie Boys - Todos los derechos reservados</p>
    </footer>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  components: { Navbar }
}
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
}
.footer {
  background: #222;
  color: #fff;
  text-align: center;
  padding: 1rem;
  margin-top: 2rem;
}
</style>

