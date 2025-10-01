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
:root {
  --bg: #aeff00;
  --accent: #ff5a5f;
  --accent-2: #ffb86b;
  --muted: #9aa4b2;
  --card: #c8ff00;
  --dark: #000030;
  --darker: #0a0720;
}

body {
  margin: 0;
  font-family: 'Montserrat', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
  background: linear-gradient(180deg, var(--darker) 0%, var(--dark) 60%);
  color: #e6eef6;
  min-height: 100vh;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

.footer {
  background: linear-gradient(90deg, #ff5a5f, #ff7a59);
  color: #fff;
  text-align: center;
  padding: 1rem;
  margin-top: auto;
  font-size: 0.9rem;
}
</style>
