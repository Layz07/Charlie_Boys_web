<template>
  <div class="contact-page-vintage">
    <header class="vintage-header">
      <h1> Ubicación y Contacto</h1>
      <p>Estamos esperándote. ¡Contáctanos o ven a visitarnos!</p>
    </header>

    <section class="vintage-content">
      <!-- Mapa a la izquierda -->
      <div class="map-section">
        <h3>📍 Encuéntranos Aquí</h3>
        <div class="map-frame">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3869.234567890123!2d-89.2712315!3d13.6766151!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8f632e4c10ffa58d%3A0x58d9c8dddf7f62b9!2sCharlie%20Boy%20Pizza%20%26%20Grill!5e0!3m2!1ses!2ssv!4v1234567890123!5m2!1ses!2ssv"
            width="100%"
            height="400"
            style="border:0; border-radius: 8px;"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>
      </div>

      <!-- Formulario a la derecha -->
      <div class="form-section">
        <div class="contact-info">
          <h2>📞 DÉJANOS UN MENSAJE</h2>
          <div class="info-box">
            <p><strong>Información General:</strong> (503) 2562-9999</p>
          </div>
        </div>

        <div class="contact-form">
          <h3>💬 PREGÚNTANOS LO QUE QUIERAS</h3>
          <form @submit.prevent="submitForm">
            <div class="form-group">
              <input type="text" placeholder="Nombre" v-model="form.name" required />
              <input type="email" placeholder="Email" v-model="form.email" required />
            </div>
            <textarea placeholder="Comentarios..." v-model="form.message" rows="6" required></textarea>
            <button type="submit" class="send-btn">Enviar</button>
          </form>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { reactive } from 'vue';

const form = reactive({
  name: '',
  email: '',
  message: ''
});

const submitForm = () => {
  alert(`Gracias, ${form.name}! Tu mensaje ha sido enviado.`);
  form.name = '';
  form.email = '';
  form.message = '';
};
</script>

<style scoped>
/* FONDO AZUL OSCURO */
body {
  background-color: #0a0a2a;
  margin: 0;
  padding: 0;
}

.contact-page-vintage {
  padding: 40px 20px;
  max-width: 1200px;
  margin: 40px auto;
  background-color: #f9f5eb; /* Beige claro del contenedor interior */
  border-radius: 16px;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.3);
  min-height: 80vh;
}

.vintage-header {
  text-align: center;
  margin-bottom: 30px;
}

.vintage-header h1 {
  font-size: 2rem;
  margin-bottom: 10px;
  color: #5a4a42;
  font-family: 'Georgia', serif;
}

.vintage-header p {
  color: #8b7355;
  font-size: 1.1rem;
  font-style: italic;
}

.vintage-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px;
}

/* MAPA */
.map-section h3 {
  color: #5a4a42;
  margin-bottom: 15px;
  font-family: 'Georgia', serif;
  font-weight: bold;
}

.map-frame {
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
}

/* FORMULARIO */
.form-section {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.contact-info h2 {
  color: #5a4a42;
  font-size: 1.5rem;
  margin-bottom: 15px;
  font-family: 'Georgia', serif;
  text-align: center;
  letter-spacing: 1px;
}

.info-box {
  background: #fdfaf4;
  padding: 15px;
  border-radius: 8px;
  border: 1px solid #ddd;
  font-family: 'Georgia', serif;
  color: #5a4a42;
  margin-bottom: 20px;
}

.info-box p {
  margin: 8px 0;
  line-height: 1.5;
}

.info-box .link {
  color: #8b7355;
  text-decoration: underline;
  font-style: italic;
  margin-top: 10px;
  display: inline-block;
}

.contact-form h3 {
  color: #5a4a42;
  margin-bottom: 15px;
  font-family: 'Georgia', serif;
  text-align: center;
}

.form-group {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-bottom: 15px;
}

.form-group input,
textarea {
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 6px;
  font-family: 'Georgia', serif;
  background: #fff;
  color: #333;
}

textarea {
  grid-column: 1 / -1;
  min-height: 120px; /* Campo de comentarios más alto */
}

.send-btn {
  width: 100%;
  padding: 12px;
  background: #8b7355;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  font-family: 'Georgia', serif;
  font-weight: bold;
  transition: background 0.3s;
}

.send-btn:hover {
  background: #5a4a42;
}

@media (max-width: 768px) {
  .vintage-content {
    grid-template-columns: 1fr;
  }

  .form-group {
    grid-template-columns: 1fr;
  }
}
</style>