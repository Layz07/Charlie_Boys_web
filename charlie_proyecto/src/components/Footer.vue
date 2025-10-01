<template>
  <footer class="footer">
    <div class="footer-content">
      <!-- Logo a la izquierda -->
      <div class="footer-left">
        <img src="@/assets/Logo charlie.png" alt="Logo" class="footer-logo" />
      </div>

    <div class="footer-center">
      <p> C. La Libertad, Cd Merliot</p>
      <p>+503 2562-9999</p>
    </div>


      <!-- Redes sociales a la derecha -->
      <div class="footer-right">
        <a href="https://facebook.com/" target="_blank" rel="noopener noreferrer">
          <i class="fab fa-facebook"></i>
        </a>
        <a href="https://instagram.com/" target="_blank" rel="noopener noreferrer">
          <i class="fab fa-instagram"></i>
        </a>
      </div>
    </div>

    <!-- Línea separadora -->
    <hr class="footer-divider" />

    <!-- Derechos reservados -->
    <p class="footer-text">© 2025 Charlie Boys - Todos los derechos reservados</p>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #111;
  color: #fff;
  padding: 20px 30px;
  text-align: center;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.footer-left {
  display: flex;
  align-items: center;
}

.footer-logo {
  width: 50px;
  height: auto;
}

.footer-right {
  display: flex;
  gap: 15px;
  font-size: 1.3rem;
}

.footer-right a {
  color: #fff;
  transition: 0.3s;
}

.footer-right a:hover {
  color: #f39c12;
}

.footer-divider {
  border: 0;
  border-top: 1px solid #444;
  margin: 15px 0;
}

.footer-contact {
  margin-bottom: 10px;
  font-size: 0.9rem;
  line-height: 1.5;
}

.footer-text {
  font-size: 0.85rem;
  margin-top: 5px;
}
</style>
