<template>
  <div class="delivery-page-full">
    <header class="main-header">
      <h1>🍔 Charlie Boys Delivery</h1>
      <button class="cart-btn" @click="toggleCart">
        🛒 Carrito ({{ cart.length }})
      </button>
    </header>

    <!-- Categorías -->
    <section class="categories">
      <button
        v-for="cat in categories"
        :key="cat.id"
        :class="{ active: activeCategory === cat.id }"
        @click="activeCategory = cat.id"
      >
        {{ cat.name }}
      </button>
    </section>

    <!-- Productos -->
    <section class="menu-grid">
      <div
        v-for="item in filteredProducts"
        :key="item.id"
        class="menu-item"
      >
        <img :src="item.image" :alt="item.name" />
        <div class="item-info">
          <h3>{{ item.name }}</h3>
          <p class="price">${{ item.price.toFixed(2) }}</p>
          <button
            @click="addToCart(item)"
            :class="{ pulse: pulseButton === item.id }"
            class="add-btn"
          >
            Agregar +
          </button>
        </div>
      </div>
    </section>

    <!-- Carrito lateral -->
    <aside class="cart-sidebar" :class="{ open: cartOpen }">
      <div class="cart-header">
        <h2>🛒 Tu Pedido</h2>
        <button @click="toggleCart" class="close-btn">✕</button>
      </div>

      <div class="cart-items">
        <div v-for="item in cart" :key="item.id" class="cart-item">
          <div class="item-details">
            <span>{{ item.name }}</span>
            <div class="quantity-controls">
              <button @click="updateQuantity(item, -1)" class="qty-btn">−</button>
              <span class="qty">{{ item.quantity }}</span>
              <button @click="updateQuantity(item, 1)" class="qty-btn">+</button>
            </div>
          </div>
          <div class="item-price">
            <span>${{ (item.price * item.quantity).toFixed(2) }}</span>
            <button @click="removeFromCart(item.id)" class="remove-btn">✕</button>
          </div>
        </div>

        <div v-if="cart.length > 0" class="cart-actions">
          <button @click="clearCart" class="clear-btn">🗑️ Vaciar Carrito</button>
        </div>

        <p v-if="cart.length === 0">Tu carrito está vacío</p>
      </div>

      <div class="cart-total">
        <strong>Total: ${{ total.toFixed(2) }}</strong>
      </div>

      <form @submit.prevent="placeOrder" class="delivery-form">
        <h3>📝 Datos de Entrega</h3>
        <input type="text" placeholder="Nombre completo" v-model="order.name" required />
        <input type="text" placeholder="Dirección exacta" v-model="order.address" required />
        <input type="tel" placeholder="Teléfono (ej: +503 1234-5678)" v-model="order.phone" required />
        <textarea placeholder="Instrucciones de entrega (opcional)" v-model="order.notes"></textarea>
        <button type="submit" class="order-btn">🚀 Realizar Pedido</button>
      </form>
    </aside>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Categorías
const categories = [
  { id: 'all', name: 'Todo' },
  { id: 'fastfood', name: 'Comida Rápida' },
  { id: 'pizza', name: 'Pizzas' },
  { id: 'drinks', name: 'Bebidas' },
  { id: 'desserts', name: 'Postres' }
];

const activeCategory = ref('all');

// Productos de ejemplo
const products = [
  { id: 1, name: 'Hamburguesa Mushroom Alfredo Parmesano', price: 6.95, category: 'fastfood', image: 'https://libritasdemas.com/wp-content/uploads/2018/02/16-1.jpg' },
  { id: 2, name: 'Pizza Clasica', price: 12.99, category: 'pizza', image: 'https://media.discordapp.net/attachments/1090880697134219324/1432745312228999330/image.png?ex=69022b8d&is=6900da0d&hm=137face592363ddefe1dbd1fd77f9035199f80a170410a7a0094405205cfab55&=&format=webp&quality=lossless' },
  { id: 3, name: 'Coca-Cola', price: 1.99, category: 'drinks', image: 'https://media.chevronextramile.com/uploads/2021/04/26095210/Coke_20oz-800x800.jpg' },
  { id: 4, name: 'Empanaditas de Nutella', price: 3.75, category: 'desserts', image: 'https://libritasdemas.com/wp-content/uploads/2018/02/18.jpg' },
  { id: 5, name: 'Bolitas de camaron y queso.', price: 2.99, category: 'fastfood', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQTyc7pZoY2XEJn8Wo_-a2q9JjyDcLVKu1kTA&s' },
  { id: 6, name: 'Hot dog', price: 4.50, category: 'fastfood', image: 'https://cdn.discordapp.com/attachments/1359932476138455364/1432744697243111557/Hotdog.png?ex=69022afa&is=6900d97a&hm=b4b021c5be25cbaa17a89a1e3302b8284a9b6af3e218693ca97e4025d42a63e2&' },
  { id: 7, name: 'Pizza Personal', price: 5.99, category: 'pizza', image: 'https://media.discordapp.net/attachments/1090880697134219324/1432746394032013383/image.png?ex=69022c8f&is=6900db0f&hm=0bd2d3f22c0993fbf3c590dcd8c049e9112e02bda871d86308fdaf15c1966caa&=&format=webp&quality=lossless' }
];

// Filtrar productos por categoría
const filteredProducts = computed(() => {
  if (activeCategory.value === 'all') return products;
  return products.filter(p => p.category === activeCategory.value);
});

// Carrito
const cart = ref([]);
const cartOpen = ref(false);

// Efecto de pulsación
const pulseButton = ref(null);

const addToCart = (item) => {
  const existing = cart.value.find(i => i.id === item.id);
  if (existing) {
    existing.quantity++;
  } else {
    cart.value.push({ ...item, quantity: 1 });
  }

  // Activar efecto de pulsación
  pulseButton.value = item.id;
  setTimeout(() => {
    pulseButton.value = null;
  }, 300);
};

const removeFromCart = (id) => {
  cart.value = cart.value.filter(item => item.id !== id);
};

const updateQuantity = (item, change) => {
  item.quantity += change;
  if (item.quantity <= 0) {
    removeFromCart(item.id);
  }
};

const clearCart = () => {
  if (confirm('¿Estás seguro de vaciar el carrito?')) {
    cart.value = [];
  }
};

const total = computed(() =>
  cart.value.reduce((sum, item) => sum + item.price * item.quantity, 0)
);

const toggleCart = () => {
  cartOpen.value = !cartOpen.value;
};

// Pedido
const order = ref({
  name: '',
  address: '',
  phone: '',
  notes: ''
});

const placeOrder = () => {
  if (cart.value.length === 0) {
    alert('Tu carrito está vacío');
    return;
  }
  alert(`🎉 ¡Pedido confirmado!\nTotal: $${total.value.toFixed(2)}\nEntrega a: ${order.value.name}\nGracias por elegir Charlie Boys!`);
  cart.value = [];
  order.value = { name: '', address: '', phone: '', notes: '' };
  cartOpen.value = false;
};
</script>

<style scoped>
.delivery-page-full {
  background: #0a0a15;
  color: white;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  min-height: 100vh;
  padding: 20px;
}



.main-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding: 15px 0;
  border-bottom: 1px solid #333;
}

.main-header h1 {
  font-size: 1.8rem;
  color: #ff4d4d;
  font-weight: bold;
}

.cart-btn {
  background-color: #ff4d4d;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s;
}

.cart-btn:hover {
  background: #e63c3c;
}

.categories {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
  flex-wrap: wrap;
  overflow-x: auto;
  padding: 10px 0;
}

.categories button {
  padding: 8px 16px;
  background: #1a1a2e;
  color: white;
  border: 1px solid #333;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.3s;
}

.categories button.active {
  background: #ff4d4d;
  color: white;
  border-color: #ff4d4d;
}

.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
  margin-bottom: 40px;
}

.menu-item {
  background: #1a1a2e;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s;
  cursor: pointer;
}

.menu-item:hover {
  transform: translateY(-5px);
}

.menu-item img {
  width: 100%;
  height: 300px;
  object-fit: cover;
}

.item-info {
  padding: 15px;
  text-align: center;
}

.item-info h3 {
  font-size: 1.2rem;
  margin: 0 0 8px 0;
  color: white;
}

.item-info .price {
  font-size: 1.1rem;
  color: #ff4d4d;
  font-weight: bold;
  margin: 0 0 10px 0;
}

.add-btn {
  background-color: #ff4d4d;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
  transition: background 0.3s;
}

.add-btn:hover {
  background: #e63c3c;
}

/* Efecto de pulsación */
.pulse {
  animation: pulse 0.3s ease-in-out;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.1); }
  100% { transform: scale(1); }
}

/* Carrito lateral */
.cart-sidebar {
  position: fixed;
  top: 0;
  right: -400px;
  width: 380px;
  height: 100%;
  background: #1a1a2e;
  box-shadow: -4px 0 10px rgba(0, 0, 0, 0.5);
  transition: right 0.3s ease-in-out;
  z-index: 1000;
  padding: 20px;
  overflow-y: auto;
  border-left: 2px solid #ff4d4d;
}

.cart-sidebar.open {
  right: 0;
}

.cart-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding-bottom: 10px;
  border-bottom: 1px solid #333;
}

.cart-header h2 {
  color: #ff4d4d;
  font-size: 1.4rem;
}

.close-btn {
  background: none;
  border: none;
  font-size: 1.5rem;
  color: #ff4d4d;
  cursor: pointer;
}

.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 0;
  border-bottom: 1px solid #333;
  color: white;
}

.item-details {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.quantity-controls {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 8px;
}

.qty-btn {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 1px solid #ff4d4d;
  background: #222;
  color: white;
  cursor: pointer;
  font-weight: bold;
}

.qty {
  min-width: 30px;
  text-align: center;
}

.remove-btn {
  background: none;
  border: none;
  color: #ff4d4d;
  cursor: pointer;
  font-size: 1.2rem;
  margin-left: 10px;
}

.cart-actions {
  margin: 20px 0;
}

.clear-btn {
  background: #e63c3c;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 6px;
  cursor: pointer;
  font-weight: bold;
  width: 100%;
}

.clear-btn:hover {
  background: #cc2b2b;
}

.cart-total {
  margin: 20px 0;
  font-size: 1.3rem;
  font-weight: bold;
  color: #ff4d4d;
  text-align: center;
}

.delivery-form input,
.delivery-form textarea {
  width: 100%;
  padding: 12px;
  margin: 8px 0;
  border: 1px solid #333;
  border-radius: 8px;
  background: #222;
  color: white;
  font-size: 1rem;
  transition: border 0.3s;
}

.delivery-form input:focus,
.delivery-form textarea:focus {
  border-color: #ff4d4d;
  outline: none;
}

.order-btn {
  width: 100%;
  padding: 15px;
  background-color: #ff4d4d;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 1.1rem;
  font-weight: bold;
  margin-top: 15px;
  transition: background 0.3s;
}

.order-btn:hover {
  background: #e63c3c;
}

@media (max-width: 768px) {
  .menu-grid {
    grid-template-columns: 1fr;
  }

  .cart-sidebar {
    width: 100%;
  }

  .main-header h1 {
    font-size: 1.4rem;
  }
}
</style>