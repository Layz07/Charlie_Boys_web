<template>
  <div class="login-page">
    <!-- Fondo -->
    <div class="background"></div>
    <div class="overlay"></div>

    <!-- Contenedor del login -->
    <div class="login-container">
      <!-- Imagen lateral -->
      <div class="login-image">
        <img src="@/assets/Logo charlie.png" alt="login side" />
      </div>

      <!-- Formulario -->
      <div class="login-form">
        <h2>Login</h2>
        <form>
          <input type="email" placeholder="Email" />
          <input type="password" placeholder="Password" />

          <a href="#" class="forgot-password">¿Olvidaste tu contraseña?</a>

          <button type="submit" class="btn-login">Ingresar</button>

          <div class="divider">OR</div>

          <button type="button" class="btn-register">Registrarse</button>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Fondo con imagen */
.login-page {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: Arial, sans-serif;
}

.background {
  position: absolute;
  inset: 0;
  background: url("@/assets/Logo charlie.png")
    no-repeat center center/cover;
  z-index: -2;
}

.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to right, rgba(255, 0, 0, 0.5), rgba(255, 200, 0, 0.5));
  z-index: -1;
}

/* Contenedor principal */
.login-container {
  display: flex;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0px 6px 20px rgba(0, 0, 0, 0.3);
  max-width: 850px;
  width: 100%;
}

/* Imagen lateral */
.login-image {
  flex: 1;
  display: none;
}
.login-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
@media (min-width: 768px) {
  .login-image {
    display: block;
  }
}

/* Formulario */
.login-form {
  flex: 1;
  padding: 40px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.login-form h2 {
  text-align: center;
  margin-bottom: 20px;
  color: #d32f2f;
  font-size: 28px;
}

/* Inputs */
.login-form input {
  width: 100%;
  padding: 12px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 8px;
  outline: none;
  font-size: 16px;
}
.login-form input:focus {
  border-color: #d32f2f;
}

/* Links */
.forgot-password {
  font-size: 14px;
  color: #555;
  text-decoration: none;
  display: block;
  text-align: right;
  margin-bottom: 15px;
}
.forgot-password:hover {
  color: #d32f2f;
}

/* Botones */
.btn-login {
  width: 100%;
  padding: 12px;
  background: #d32f2f;
  color: white;
  font-weight: bold;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
}
.btn-login:hover {
  background: #b71c1c;
}

.btn-register {
  width: 100%;
  padding: 12px;
  background: #ddd;
  color: #333;
  font-weight: bold;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
}
.btn-register:hover {
  background: #bbb;
}

/* Divider */
.divider {
  text-align: center;
  margin: 15px 0;
  font-size: 14px;
  color: #888;
  position: relative;
}
.divider::before,
.divider::after {
  content: "";
  position: absolute;
  top: 50%;
  width: 40%;
  height: 1px;
  background: #ccc;
}
.divider::before {
  left: 0;
}
.divider::after {
  right: 0;
}
</style>
