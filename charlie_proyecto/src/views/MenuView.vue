<template>
  <div class="charlie-home">
    <div class="menu-container">
      <div class="menu-header">
        <div class="header-decoration"></div>
        <h1 class="menu-title">Nuestro Menú</h1>
        <p class="menu-subtitle">Pizzas especiales con ingredientes únicos</p>
        <div class="header-ornament">
          <span class="ornament-dot"></span>
          <span class="ornament-line"></span>
          <span class="ornament-dot"></span>
        </div>
        
        <!-- Botón del carrito -->
        <button class="cart-btn" @click="toggleCart">
          🛒 Carrito ({{ cart.length }})
        </button>
      </div>
      
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
          <div
            v-for="pizza in pizzas"
            :key="pizza.id"
            class="menu-item"
            :class="{ featured: pizza.featured }"
          >
            <img :src="pizza.image" :alt="pizza.name" class="item-image" />
            <div v-if="pizza.badge" :class="['item-badge', pizza.badgeClass]">
              {{ pizza.badge }}
            </div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">{{ pizza.name }}</h3>
                <p v-if="pizza.desc" class="item-description">
                  {{ pizza.desc }}
                </p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">Personal</span>
                  <span class="price">${{ pizza.priceP.toFixed(2) }}</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Grande</span>
                  <span class="price highlight">${{ pizza.priceG.toFixed(2) }}</span>
                </div>
              </div>
              
              <!-- Botones de agregar al carrito -->
              <div class="add-to-cart-buttons">
                <button @click="addToCart({ ...pizza, size: 'Personal', price: pizza.priceP })" class="add-btn">
                  Agregar Personal +
                </button>
                <button @click="addToCart({ ...pizza, size: 'Grande', price: pizza.priceG })" class="add-btn">
                  Agregar Grande +
                </button>
              </div>
              
            </div>
          </div>
          </div>
      </section>
      <section v-show="activeCategory === 'hamburguesas'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">02</span>
            <h2 class="section-title">Hamburguesas</h2>
          </div>
          <div class="price-legend">
            <div class="legend-item">
              <span class="legend-icon">🍔</span>
              <span class="size-label">1 Carne (6oz)</span>
            </div>
            <div class="legend-item">
              <span class="legend-icon">🍔</span>
              <span class="size-label">Doble (12oz)</span>
            </div>
          </div>
        </div>
        <div class="menu-grid">
          <div
            v-for="burger in hamburguesas"
            :key="burger.id"
            class="menu-item"
            :class="{ featured: burger.featured }"
          >
            <img :src="burger.image" :alt="burger.name" class="item-image" />
            <div v-if="burger.badge" :class="['item-badge', burger.badgeClass]">
              {{ burger.badge }}
            </div>
            <div class="item-content">
              <div class="item-info">
                <h3 class="item-name">{{ burger.name }}</h3>
                <p v-if="burger.desc" class="item-description">
                  {{ burger.desc }}
                </p>
                <div class="item-divider"></div>
              </div>
              <div class="item-prices">
                <div class="price-box">
                  <span class="price-label">1 Carne</span>
                  <span class="price">${{ burger.priceP.toFixed(2) }}</span>
                </div>
                <div class="price-box">
                  <span class="price-label">Doble Carne</span>
                  <span class="price highlight">${{ burger.priceG.toFixed(2) }}</span>
                </div>
              </div>
              
              <!-- Botones de agregar al carrito -->
              <div class="add-to-cart-buttons">
                <button @click="addToCart({ ...burger, size: '1 Carne', price: burger.priceP })" class="add-btn">
                  Agregar 1 Carne +
                </button>
                <button @click="addToCart({ ...burger, size: 'Doble', price: burger.priceG })" class="add-btn">
                  Agregar Doble +
                </button>
              </div>
              
            </div>
          </div>
          </div>
      </section>
      <section v-show="activeCategory === 'bebidas'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">03</span>
            <h2 class="section-title">Bebidas</h2>
          </div>
        </div>
        <div class="drinks-grid">
          <div v-for="bebida in bebidas" :key="bebida.id" class="drink-item" :class="{ featured: bebida.featured }">
            <img v-if="bebida.image" :src="bebida.image" class="drink-icon-img" :alt="bebida.name" />
            <div v-else class="drink-icon">{{ bebida.icon }}</div>
            <div class="drink-info">
              <h3 class="drink-name">{{ bebida.name }}</h3>
              <p v-if="bebida.desc" class="drink-description">{{ bebida.desc }}</p>
            </div>
            <div class="drink-price">${{ bebida.price.toFixed(2) }}</div>
            
            <!-- Botón de agregar al carrito -->
            <button @click="addToCart({ ...bebida, size: '', price: bebida.price })" class="add-btn">
              Agregar +
            </button>
            
          </div>
        </div>
      </section>
<section v-show="activeCategory === 'shakes'" class="menu-section">
  <div class="section-header">
    <div class="section-title-wrapper">
      <span class="section-number">04</span>
      <h2 class="section-title">Shakes</h2>
    </div>
  </div>
  <div class="shakes-grid">
    <div
      v-for="shake in shakes"
      :key="shake.id"
      class="shake-card"
      :class="{ premium: shake.premium, tropical: shake.tropical, fresh: shake.fresh }"
    >
      <div v-if="shake.badge" :class="['shake-badge', shake.badgeClass]">
        {{ shake.badge }}
      </div>
      <div class="shake-header">
        <img v-if="shake.image" :src="shake.image" class="shake-image" :alt="shake.name" />
        <span v-else class="shake-icon">{{ shake.icon }}</span>
        <h3 class="shake-name">{{ shake.name }}</h3>
        <p v-if="shake.desc" class="shake-desc">{{ shake.desc }}</p>
      </div>
      <!-- Nuevo contenedor para precio y botón -->
      <div class="shake-footer">
        <span class="shake-price">${{ shake.price.toFixed(2) }}</span>
        <!-- Botón de agregar al carrito -->
        <button @click="addToCart({ ...shake, size: '', price: shake.price })" class="add-btn">
          Agregar +
        </button>
      </div>
    </div>
  </div>
</section>
      <section v-show="activeCategory === 'hotdogs'" class="menu-section">
        <div class="section-header">
          <div class="section-title-wrapper">
            <span class="section-number">05</span>
            <h2 class="section-title">Hot Dogs</h2>
          </div>
        </div>
        <div class="hotdogs-grid">
          <div v-for="hotdog in hotdogs" :key="hotdog.id" class="hotdog-item">
            <img v-if="hotdog.image" :src="hotdog.image" class="hotdog-icon-img" :alt="hotdog.name" />
            <div v-else class="hotdog-icon">{{ hotdog.icon }}</div>
            <div class="hotdog-info">
              <h3 class="hotdog-name">{{ hotdog.name }}</h3>
              <p v-if="hotdog.desc" class="hotdog-description">{{ hotdog.desc }}</p>
            </div>
            <div class="hotdog-price">${{ hotdog.price.toFixed(2) }}</div>
            
            <!-- Botón de agregar al carrito -->
            <button @click="addToCart({ ...hotdog, size: '', price: hotdog.price })" class="add-btn">
              Agregar +
            </button>
            
          </div>
        </div>
      </section>
    </div>
    
    <!-- Carrito lateral -->
    <aside class="cart-sidebar" :class="{ open: cartOpen }">
      <div class="cart-header">
        <h2>🛒 Tu Pedido</h2>
        <button @click="toggleCart" class="close-btn">✕</button>
      </div>

      <div class="cart-items">
        <div v-for="item in cart" :key="item.id" class="cart-item">
          <div class="item-details">
            <span>{{ item.name }} ({{ item.size }})</span>
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

<script>
export default {
  name: "MenuView",
  data() {
    return {
      activeCategory: "pizzas",
      categories: [
        { id: "pizzas", label: "Pizzas", icon: "🍕" },
        { id: "hamburguesas", label: "Burgers", icon: "🍔" },
        { id: "bebidas", label: "Bebidas", icon: "🥤" },
        { id: "shakes", label: "Shakes", icon: "🥤" },
        { id: "hotdogs", label: "Hot Dogs", icon: "🌭" },
      ],
      // --- DATA DINÁMICA DE PRODUCTOS ---
      pizzas: [
        {
          id: 1,
          name: "Pizza de un ingrediente especial",
          desc: null,
          priceP: 9.50,
          priceG: 12.50,
          badge: "Personalizable",
          badgeClass: "",
          image: "https://dynamic-media-cdn.tripadvisor.com/media/photo-o/18/a3/23/83/ta-img-20190804-133408.jpg?w=800&h=-1&s=1",
        },
        {
          id: 2,
          name: "Chicken Alfredo",
          desc: "salsa Alfredo, pollo, hongos frescos",
          priceP: 9.75,
          priceG: 12.95,
          badge: "Popular",
          badgeClass: "popular",
          featured: true,
          image: "https://lh3.googleusercontent.com/rd-gg-dl/ABS2GSmQBdooieOs8SO3hVSXOdsGxhu1undHX5SayFiyskBj2PXODl9jWVhZjPjKTUHb9IuFWTeJjebJLw9k8V7dNV1Z_FlPj8Z66Q859ATHNWxoB2685_znXzGizOsWu67Z2q1T5iwY9biRIoh1EPwyTjrovo9WrgqTFagtE0aAS69fLyNaQ--LX_TFYlpLUenqYFeOrwVxSHhjSseV8SJ3FoQdv5xecCalcD2ksgxBSB4PIuhNSZi-5EvJetosy92LIpe5_99RZl_FZeA-KjE8OowhIdwS1ckxbDfh0VcD8OSqd2epz_qbXuf2tLjxMzHGeOzKqMEQJZa9VLsYry2xlph7GEuEplkl_09-PjvkVYPyEdeaoP90omJpePhTM8Z4v1jbFMa5c34c17t8SrVgidkQRvS-qQJjs4xb4Gn5Ebbzgtd5KjrRzzO-5PkkaitgTm_jWvxszc0LotyP2k2a46j40iScUUK5Yry1ryizCAQgtzOXZthgr3U_LAIQeWEo7JdD-yGLQoZ5KGNG5w8dTq9xi2bY_h26nRj3QxkbCuxUDMNl6XT_7VPDbgImCXyhCNjLo_biDTSTvsAvSmm-lAxf_x1lspAzd-hk-PpsjvgFVQBcBbQeC4u3Z_CbeQDqwvExCPpBu_-2ATpB3nHV3Sk5VOVuwefYbBja8l1P-9Qr_Ow9yrLd4E8EOlBpzhiVS3VXQtQkcQj2arRSkfI6O6PhCD0qY-f89y1LLn9UymZUYhd3W1i6gQDM8bxmwdCXphcQxiNtwvLixdH-kJiszBySCHQWPzc2HPZTifW6QeAFge7cqra4U-0agrPNujPZXG_6kBla5Kp6uT5sFuTt3T2j_zMX4c5nlKgiEPPtUSoJcVd1joWsMInhAX-eFliqbXtx-b6srfLjDxFvwwpvCtUrahKNf5LL4xmlHv8I0Juq0eV2v4CmE1Ogo9hZBjNDlSzWQ6gipLfGPLlip7eVjnw4925s8z-6aOfr0h8KwMsrC5u83Al4GWsvwDj8SOkisXMoQ3MRdXnk-kFGxWNfVfpPlFoFgkFp4zxmnMLlDYioC8BeHxOzWBnHct2tO_mYOFzsv5g6oWgnapnu0nLiaTbWnEEDMp8hCjL2np0XSNkK52qSIB-wgV1mh9NLM9bUNuy8vITn20drlzq7vjZ2ctjCLfUqkDrPU9I0kQYmolRXR2rp_lPhLea8qDfNncuFV7JN9JN_WWs969USerA5dQNV_A83V7j9NfSApZxjcUHL8wREyezQeGHc_fwDRiQj_c0Umx3ZB8c=s1024-rj",
        },
        {
          id: 3,
          name: "Chicken Buffalo",
          desc: "Pollo y salsa Buffalo",
          priceP: 8.95,
          priceG: 11.95,
          badge: "Picante 🌶️",
          badgeClass: "spicy",
          image: "https://lh3.googleusercontent.com/rd-gg-dl/ABS2GSmM315yj8Q8hdZusDWXldLltlpWFRfARvaeO_mtFvxC5Bpr4WVI9yahQ9tiJcO1-rHK6QgHlZPoLS0ega6YkEPD_7vQ5G2eDRItRJWYAdj-A6FHxT13Q8Gr-B4C8bqVvVgI1htYPPylV460FAo_4zt4iO7tdWfgmeGg1KuzHlC6LMyxPptTwDSnDwuBpHESiOaEG-Edb6XWyILRXRFYUf-hiiKG6YwEw5kuLg5_4uqWRD7IHL_YUoXAPgZabF9gTx7dKSn4zxwMTqdt8cxakfoC98itQMfYex84CCtcqKbs0PDngH4T8YmWuZeUnse-B1lgcADABQCcbh0ByY8x7Vsob_XB5tl_RT6pwFxV_yfkiFglM85DsNcAm0FHu7ZBjJ6nDa2WJLLYqgrBsjTu8yLsFmLGysPNk2MjEjfJnncuf19LcS577P2h0h6VSdTweEVEkD161YPNRFBPvq8MmfcAfKAa4x9dgUduKHPdS8g3Ihf3T7LHVNSdbweeV4Fup7v1uatsGwV7qIxjQqNhgc8tHaj4WZmM6-d40hN9xDUiQrrhq6u_sz3m-PMEiCzRQYED53gyRm4O5pzjDVMvP6XcbmA29oLPgbjJpZKpGzXTHPcsJRiRWLbMZe7FdvZnC_eEOmseiZnQa1XHHecOzdBrHst27yD_FScek3HKErFuIUBS7JqCGEOlcQ3WKaOOCima7sKGdC5VORI9Na7ByvOdeTv6MErH60KRrET7So6kDbaqfG6J2hLDeVqCu0Jb32fssjGC3T3xxm8ARsOUc2rodHr4stdpoMHx6e4yPsYOxTufWNLZlQ184L3Qxa4RTaQAHBb7OmASP-KvyYSmR13X7XcpE7Snmaj3Nrw4yG5xnOW2UQvbSfB7Nh5PXnGaVa1gijWB-xcGfnul7NWF8C6P_U5htvzzQxJ8O3Ow7unyu5JE23_D5X_lbvEvPi0_qASwmyjXLOCtTCfOuclijzKcmpiwiKDV-VLTa-r99l6Jw0TOaJJsT88wcMfo7LET94GqJ-gZ6LW-OF57t-Fb6Ya-b7_0v3UbaN3H8KXGo7LK8Ed7hKUMBolHsWqnZP0McdvdfpKGRSlVP-apcw1nRWn32lEatJzsYSWK_gOU7dQLa-BWrx1g2Y_V5cL0G9_PrAo517kHDBfXxgVTysD3tqviwz8hSKK6wljKa3uMySKqIIP7ioqU8XY6XYlGVmud5Nh6eK4tGYatXqd5DWtumur2-osQ85y8a7Ku0TleyzXicfGQWDWD6ArZauc2gXKyJ7lED0XDlDE=s1024-rj",
        },
        {
          id: 4,
          name: "Tijuana",
          desc: "Doritos, Carne Asada, lechuga",
          priceP: 11.95,
          priceG: 16.95,
          badge: "Especial",
          badgeClass: "special",
          featured: true,
          image: "https://lh3.googleusercontent.com/rd-gg-dl/ABS2GSk73uNI3n5pbM6-95zG17Ub9uFsG-LEcaDTEYsJXW_9nRrN5Kdp6KWMhW4CilKDS7fZ4qk1HLyzFWBdAx9yczkEYll0_LFv8Wrmw6A4RtZSnuio48u7_wSdIZw7M7hvOD7cBYy_Ri_PylzuczzBa6j6JJtA_AYBvCHBKdf_cV0dvqjQ4g37wIsb8fcVz5oyscOAsRg979TzThgEqXJI65dKJkI3_JT3wj7IyQQnV0xmutpdqFPVll8sZqxBIQNx7vIiqLbbujCaLNtwtAD2gfokNL333OPUC2cI7Zcb24TeGzvL70kv-SLVGcrTKndplF5iZ14ZfjgzIJ1WF0bBF8nPERukUk-SYgNYUIUP05vE1YVlQnJRZWg6vRzJtqcTKuSHro5d6ZvufyL6LFfeGOsYEQDvnrS2ISh4q640qo4AmIqqYwQOZG32gYY9YClwVU2l59302TwbYzdO-Orx1tniTnVcD5OlK6b615fZyz7479MtZeFD5Yg0xBxdYSh3bsuv5lWSlTt9MtLyQdwj40PscW4guBJoiFJiW8yU8haeIgHwNw7AD7twEjdFKgeBUvg-nih2EU7M6NyupUD1v9O2uz8MDL3dO_puzNGgHK19_zRbQ_w5dN25VYzxw0OV6qyTEn8jw3hWJzxhPntB-IHlTHidMJDuaLpE_Ji22VUggd9gAbe5KTegMbewqYvywr7oyrUsQdDiGudO5kNwbQ-JTW4evcJS67MYmB4xjPqV75V8L8kAFwmgtvWBtKqLV5lWqd4UMbrSGsjHiYHO03TcBmyX2Ghc6rOvzkV2z3-8GlDScFhWVxFZXTCXsY-9JRB-W4ZYU_3Csz60dy3mUk8sC_vJk5XM0wZqoCzCKfsHd2DpEkpSzg2ACvLriVz5VPj0pVjEki7uvPR8Lfu5RTi0I3Twq2LRu_jb57E6sHh_HaPmXh-h5sJhKUOtKPH7jE6q74Uy_Hy9nps6Bpeh2GiaRVpXDRKw3ma_QMEI4AztkwLDO3U6SsDRLVKGvueEmWf4MpAH-IYLFftYxvJVHs9RLT4I4elIJYkt7uU5NDUzJB7T-NH8BdxVaB4frWovPUwKFf3w9yAip3fmn_kct8q6MKq49WTANLzPiAY7pvh7opDgVd6tiLrS7AjK0I0irMZXnFcGrzshiqFERu8egz0LUqhpryDHvwIkQ1qttYtqWUJFN2PS3i79MqQ_duc5vSAXSRJhhLgR5fUjJBx0CZvCSwuVeHudS4ap7Y2CbpeyjlANlYOiJT64vO342VbNhkWWAyHgwoM=s1024-rj",
        },
        {
          id: 5,
          name: "Madrid",
          desc: "Jamón Serrano, aceitunas verdes",
          priceP: 9.95,
          priceG: 13.95,
          badge: "Premium",
          badgeClass: "premium",
          image: "https://media.discordapp.net/attachments/1090880697134219324/1432778935099461752/ABS2GSkSP586y1-KfIYKjwpwz-VEjTthOzJ1HKZTYUoH--A2i2pd3JA2MGIZ2RdAdq-aUZajCxsfI9rab7lBYP_euL1JZxmS5Ha_HF3-3vohygKOgUfE2uZKNoklvCEN1BcUHQCPmD4XYJ6E_-nulWhm57ABoC3ZCZhgE-W4Cgx7QRC6TdJiFAs1024-rj.png?ex=69024add&is=6900f95d&hm=77912879fc2c00f2852108fae39e7f6e5c45c571f682413c0c7dd50aa7d718ae&=&format=webp&quality=lossless&width=960&height=960",
        },
        {
          id: 6,
          name: "Loroco",
          desc: "Loroco, Salsa Blanca",
          priceP: 8.50,
          priceG: 11.50,
          badge: "Local",
          badgeClass: "local",
          image: "https://dynamic-media-cdn.tripadvisor.com/media/photo-o/11/8e/25/26/pizza-de-loroco-y-salsa.jpg?w=1000&h=-1&s=1",
        },
        {
          id: 7,
          name: "Vegetariana",
          desc: "Zuccini, pimientos asados, hongos frescos, aceite de oliva",
          priceP: 8.90,
          priceG: 12.50,
          badge: "Vegetariana 🌱",
          badgeClass: "veggie",
          image: "https://media.discordapp.net/attachments/1090880697134219324/1432779346145312819/ABS2GSm6J_KJHOJZiTFFoNB0BQYeXk_UhPf3akbGCKJUrSvmD3m3Bd2b8-JytZtC1EGzq3bz7pytcl6_nbggRxOML5oGNu7TvVtGerwMCElwII-7mKrSIU-wcMMsIB-Zo-66M7C_W64IBhMFrd6whZifqhUSF6vjLJB3D3-kIxg0QynJKkrbkQs1024-rj.png?ex=69024b3f&is=6900f9bf&hm=50f4b52193c36ba712548c39d0e946e31dbb8a7c5060fd0fa1b0838439ee40ca&=&format=webp&quality=lossless&width=960&height=960",
        },
        {
          id: 8,
          name: "Perla Negra",
          desc: "Calamares en su tinta y camarón salteados al ajo",
          priceP: 11.95,
          priceG: 16.95,
          badge: "Exclusiva",
          badgeClass: "exclusive",
          featured: true,
          image: "https://dynamic-media-cdn.tripadvisor.com/media/photo-o/11/8e/25/23/pizza-perla-negra.jpg?w=1000&h=-1&s=1",
        },
        // ... Agrega el resto de tus pizzas aquí ...
      ],
      hamburguesas: [
        {
          id: 401,
          name: "La Clasica Cheese Burger",
          desc: null,
          priceP: 5.25, // 1 Carne 6oz
          priceG: 7.75, // Doble Carne 12oz
          badge: "Clásica",
          badgeClass: "classic",
          image: "https://via.placeholder.com/400x200?text=Classic+Burger",
        },
        {
          id: 402,
          name: "Spicy BBQ Burger",
          desc: null,
          priceP: 5.50,
          priceG: 7.95,
          badge: "Picante 🌶️",
          badgeClass: "spicy",
          image: "https://via.placeholder.com/400x200?text=Spicy+BBQ",
        },
        {
          id: 403,
          name: "Teriyaki Burger",
          desc: null,
          priceP: 5.50,
          priceG: 7.95,
          image: "https://via.placeholder.com/400x200?text=Teriyaki+Burger",
        },
        {
          id: 404,
          name: "Franz Bacon Bawer",
          desc: null,
          priceP: 5.95,
          priceG: 8.95,
          badge: "Popular",
          badgeClass: "popular",
          featured: true,
          image: "https://via.placeholder.com/400x200?text=Bacon+Burger",
        },
        {
          id: 405,
          name: "Jalapeña Burger",
          desc: null,
          priceP: 5.75,
          priceG: 8.50,
          badge: "Picante 🌶️",
          badgeClass: "spicy",
          image: "https://via.placeholder.com/400x200?text=Jalapeño+Burger",
        },
        {
          id: 406,
          name: "La 3 Queso c/Tocino",
          desc: null,
          priceP: 5.95,
          priceG: 8.95,
          image: "https://via.placeholder.com/400x200?text=3+Quesos",
        },
        {
          id: 407,
          name: "Mushroom Alfredo Burger",
          desc: null,
          priceP: 6.50,
          priceG: 8.95,
          badge: "Especial",
          badgeClass: "special",
          featured: true,
          image: "https://libritasdemas.com/wp-content/uploads/2018/02/16-1.jpg",
        },
      ],
      bebidas: [
        {
          id: 101,
          name: "Sodas",
          desc: "Cocacola, Fanta, Sprite, Colashampan, Uva, Fresa, Crema Soda",
          price: 1.40,
          icon: "🥤",
          image: "https://via.placeholder.com/100x100?text=Sodas",
        },
        {
          id: 102,
          name: "Te Helado Lipton 354 ml",
          desc: "Durazno - Limón",
          price: 1.60,
          icon: "🧊",
          image: "https://via.placeholder.com/100x100?text=Lipton",
        },
        {
          id: 103,
          name: "Agua",
          desc: null,
          price: 1.25,
          icon: "💧",
          image: "https://via.placeholder.com/100x100?text=Agua",
        },
        {
          id: 104,
          name: "Soda de 1.5 Lts",
          desc: null,
          price: 3.95,
          icon: "🥤",
          featured: true,
          image: "https://via.placeholder.com/100x100?text=Soda+1.5L",
        },
      ],
      shakes: [
        {
          id: 201,
          name: "Nutella Milk Shake",
          desc: null,
          price: 2.95,
          icon: "🍫",
          image: "https://via.placeholder.com/150x150?text=Nutella+Shake",
        },
        {
          id: 202,
          name: "Nutella Oreo Milk Shake",
          desc: null,
          price: 3.50,
          icon: "🍪",
          badge: "Especial",
          badgeClass: "",
          premium: true,
          image: "https://via.placeholder.com/150x150?text=Oreo+Shake",
        },
        {
          id: 203,
          name: "Strawberry Milk Shake",
          desc: null,
          price: 2.95,
          icon: "🍓",
          image: "https://via.placeholder.com/150x150?text=Fresa+Shake",
        },
        {
          id: 204,
          name: "Tropical Passion",
          desc: "Vainilla, Maracuya",
          price: 3.50,
          icon: "🥭",
          badge: "Tropical",
          badgeClass: "tropical",
          tropical: true,
          image: "https://via.placeholder.com/150x150?text=Tropical",
        },
        // ... Agrega el resto de tus shakes ...
      ],
      hotdogs: [
        {
          id: 301,
          name: "Mega Hot-Dog",
          desc: null,
          price: 2.75,
          icon: "🌭",
          image: "https://via.placeholder.com/100x100?text=HotDog",
        },
        {
          id: 302,
          name: "Tex Mex Dog",
          desc: "(Salsa de queso Cheddar y jalapeños)",
          price: 3.25,
          icon: "🌶️",
          image: "https://via.placeholder.com/100x100?text=Tex+Mex",
        },
        {
          id: 303,
          name: "Dog Bacon Bawer",
          desc: "(Con nuestra deliciosa salsa blanca con tocino)",
          price: 3.50,
          icon: "🥓",
          image: "https://via.placeholder.com/100x100?text=Bacon+Dog",
        },
        // ... Agrega el resto de tus hotdogs ...
      ],
      // --- NUEVA LÓGICA DEL CARRITO ---
      cart: [],
      cartOpen: false,
      pulseButton: null, // No lo usamos aquí, pero lo puedes agregar si quieres animación
      order: {
        name: '',
        address: '',
        phone: '',
        notes: ''
      }
    };
  },
  computed: {
    total() {
      return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
    }
  },
  methods: {
    addToCart(item) {
      const existingItem = this.cart.find(i => i.id === item.id && i.size === item.size);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        this.cart.push({ ...item, quantity: 1 });
      }
    },
    removeFromCart(id) {
      // Nota: Si tienes items con el mismo ID pero distinto tamaño, necesitas un identificador único mejor.
      // Por ahora, removeremos todos con el mismo ID, lo cual puede no ser ideal si se usan tamaños.
      // Considera usar un `cartId` único generado al agregar al carrito si es necesario.
      this.cart = this.cart.filter(item => item.id !== id);
    },
    updateQuantity(item, change) {
      item.quantity += change;
      if (item.quantity <= 0) {
        this.removeFromCart(item.id);
      }
    },
    clearCart() {
      if (confirm('¿Estás seguro de vaciar el carrito?')) {
        this.cart = [];
      }
    },
    toggleCart() {
      this.cartOpen = !this.cartOpen;
    },
    placeOrder() {
      if (this.cart.length === 0) {
        alert('Tu carrito está vacío');
        return;
      }
      alert(`🎉 ¡Pedido confirmado!\nTotal: $${this.total.toFixed(2)}\nEntrega a: ${this.order.name}\nGracias por elegir Charlie Boys!`);
      this.cart = [];
      this.order = { name: '', address: '', phone: '', notes: '' };
      this.cartOpen = false;
    }
  }
};
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
  font-family: "Montserrat", system-ui, -apple-system, "Segoe UI", Roboto,
    "Helvetica Neue", Arial;
  color: #e6eef6;
  background: linear-gradient(180deg, #110b3b 0%, #000030 60%);
  min-height: 100vh;
  padding: 40px 20px 80px;
  position: relative; /* Asegura que el sidebar se posicione correctamente */
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
  background: linear-gradient(
    90deg,
    transparent,
    var(--accent),
    var(--accent-2),
    transparent
  );
  border-radius: 2px;
  box-shadow: 0 0 20px rgba(255, 90, 95, 0.5);
}
.menu-title {
  font-size: 3.5rem;
  font-weight: 800;
  background: linear-gradient(
    135deg,
    var(--accent) 0%,
    var(--accent-2) 50%,
    #ffd700 100%
  );
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

/* ESTILO DEL BOTÓN DEL CARRITO */
.cart-btn {
  position: absolute;
  top: 20px;
  right: 20px;
  background-color: var(--accent);
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
  z-index: 100;
  box-shadow: 0 4px 15px rgba(255, 90, 95, 0.4);
}

.cart-btn:hover {
  background-color: var(--accent-2);
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
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 90, 95, 0.2),
    transparent
  );
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
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.02),
    rgba(255, 255, 255, 0.03)
  );
  border-radius: 30px;
  padding: 50px 40px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4),
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
  border-bottom: 2px solid rgba(255, 90, 95, 0.2);
  position: relative;
}
.section-header::after {
  content: "";
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
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.03),
    rgba(255, 255, 255, 0.01)
  );
  border-radius: 20px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  position: relative;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
}
.menu-item::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 90, 95, 0.05),
    transparent
  );
  transition: left 0.6s;
}
.menu-item:hover::before {
  left: 100%;
}
.menu-item:hover {
  border-color: var(--accent);
  box-shadow: 0 15px 40px rgba(255, 90, 95, 0.2),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  transform: translateY(-5px);
}
.menu-item.featured {
  border-color: rgba(255, 184, 107, 0.3);
  background: linear-gradient(
    135deg,
    rgba(255, 184, 107, 0.05),
    rgba(255, 90, 95, 0.03)
  );
}
.menu-item.featured:hover {
  border-color: var(--accent-2);
  box-shadow: 0 15px 40px rgba(255, 184, 107, 0.3),
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
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
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
  font-family: "Courier New", monospace;
}
.price.highlight {
  color: var(--accent);
  text-shadow: 0 0 15px rgba(255, 90, 95, 0.5);
  font-size: 1.6rem;
}

/* ESTILO DE BOTONES DE AGREGAR AL CARRITO */
.add-to-cart-buttons {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 15px;
}

.add-btn {
  padding: 10px 15px;
  background-color: var(--accent);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
  width: 100%;
}

.add-btn:hover {
  background-color: var(--accent-2);
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
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0.03),
    rgba(255, 255, 255, 0.01)
  );
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}
.drink-item::before {
  content: "";
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
  font-family: "Courier New", monospace;
}

/* Botón de agregar en bebidas */
.drink-item > .add-btn {
  margin-left: 15px;
  align-self: center;
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
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.05),
    rgba(255, 255, 255, 0.02)
  );
  border: 2px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 30px;
  position: relative; /* Importante para z-index */
  overflow: hidden; /* Mantiene el efecto radial dentro */
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  display: flex; /* Hacemos la tarjeta un contenedor flex */
  flex-direction: column; /* Organiza elementos verticalmente */
  justify-content: space-between; /* Espacia elementos: header arriba, footer abajo */
  min-height: 350px; /* Ajusta la altura mínima para consistencia */
}
.shake-card::before {
  content: "";
  position: absolute;
  top: -50%;
  right: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(
    circle,
    rgba(255, 90, 95, 0.1) 0%,
    transparent 70%
  );
  transition: transform 0.6s ease;
  transform: scale(0);
}
.shake-card:hover::before {
  transform: scale(1);
}
.shake-card:hover {
  border-color: var(--accent);
  box-shadow: 0 20px 50px rgba(255, 90, 95, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  transform: translateY(-8px) scale(1.02);
}
.shake-card.premium {
  border-color: rgba(255, 215, 0, 0.3);
  background: linear-gradient(
    135deg,
    rgba(255, 215, 0, 0.05),
    rgba(255, 184, 107, 0.03)
  );
}
.shake-card.premium:hover {
  border-color: #ffd700;
  box-shadow: 0 20px 50px rgba(255, 215, 0, 0.3),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
}
.shake-card.tropical {
  border-color: rgba(255, 159, 64, 0.3);
  background: linear-gradient(
    135deg,
    rgba(255, 159, 64, 0.05),
    rgba(255, 206, 86, 0.03)
  );
}
.shake-card.tropical:hover {
  border-color: #ff9f40;
  box-shadow: 0 20px 50px rgba(255, 159, 64, 0.3);
}
.shake-card.fresh {
  border-color: rgba(0, 184, 148, 0.3);
  background: linear-gradient(
    135deg,
    rgba(0, 184, 148, 0.05),
    rgba(85, 239, 196, 0.03)
  );
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
  z-index: 20; /* Asegura que el badge esté por encima de todo */
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
  margin-bottom: 20px; /* Espacio antes del footer */
  z-index: 5; /* Menor que el footer */
}
.shake-icon {
  font-size: 3.5rem;
  display: block;
  margin-bottom: 15px;
  filter: drop-shadow(0 4px 10px rgba(255, 184, 107, 0.3));
  animation: float 3s ease-in-out infinite;
}
@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
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
  flex-direction: column; /* Apilar precio y botón verticalmente */
  align-items: center; /* Centrar horizontalmente */
  padding-top: 20px; /* Espacio superior */
  border-top: 1px solid rgba(255, 255, 255, 0.1); /* Línea divisoria */
  margin-top: auto; /* Empuja el footer hacia abajo */
  z-index: 10; /* Muy importante: asegura que el footer esté por encima del ::before del card */
  gap: 10px; /* Espacio entre precio y botón */
}
.shake-price {
  font-size: 2rem;
  font-weight: 900;
  background: linear-gradient(135deg, var(--accent), var(--accent-2));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-family: "Courier New", monospace;
  text-shadow: 0 0 20px rgba(255, 90, 95, 0.5);
  margin: 0; /* Eliminar márgenes por defecto */
}

/* ESTILO DE BOTONES DE AGREGAR AL CARRITO (GENERAL) */
.add-btn { /* Ajustamos el estilo general del botón */
  padding: 8px 16px;
  background-color: var(--accent); /* Color consistente */
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.3s;
  width: 100%; /* Opcional: Ocupa todo el ancho del footer */
  box-sizing: border-box; /* Incluye padding en el ancho total */
}

.add-btn:hover {
  background-color: var(--accent-2);
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
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0.03),
    rgba(255, 255, 255, 0.01)
  );
  border: 1px solid rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}
.hotdog-item::before {
  content: "";
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
  font-family: "Courier New", monospace;
}

/* Botón de agregar en hotdogs */
.hotdog-item > .add-btn {
  margin-left: 15px;
  align-self: center;
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

/* ============================================
    CSS NUEVO PARA IMÁGENES
    ============================================ */
/* Para las tarjetas de PIZZA (y HAMBURGUESAS) */
.menu-item img.item-image {
  width: 100%;
  height: 200px; /* Tú decides la altura */
  object-fit: cover;
  /* El border-radius del .menu-item ya lo redondea */
}
/* Las tarjetas de pizza/burger ahora tienen la imagen arriba y el contenido abajo */
.menu-item {
  display: flex;
  flex-direction: column;
}
.item-content {
  flex: 1; /* Asegura que todas las tarjetas tengan la misma altura */
  display: flex;
  flex-direction: column;
}
.item-info {
  flex: 1; /* Empuja los precios y botones hacia abajo */
}

/* Para las listas de BEBIDAS y HOT DOGS */
.drink-icon-img,
.hotdog-icon-img {
  width: 60px;
  height: 60px;
  border-radius: 12px;
  object-fit: cover;
  flex-shrink: 0;
  border: 1px solid rgba(255, 255, 255, 0.1);
}

/* Para las tarjetas de SHAKES */
.shake-header img.shake-image {
  width: 100px;
  height: 100px;
  border-radius: 50%; /* Círculo perfecto */
  object-fit: cover;
  margin: 0 auto 15px; /* Centrado y con espacio abajo */
  display: block;
  filter: drop-shadow(0 4px 10px rgba(255, 184, 107, 0.3));
  animation: float 3s ease-in-out infinite; /* Reutilizamos tu animación! */
}

/* ============================================
    ESTILOS DEL CARRITO LATERAL
    ============================================ */
.cart-sidebar {
  position: fixed;
  top: 0;
  right: -400px; /* Inicialmente oculto */
  width: 380px;
  height: 100%;
  background: #1a1a2e;
  box-shadow: -4px 0 10px rgba(0, 0, 0, 0.5);
  transition: right 0.3s ease-in-out;
  z-index: 1000;
  padding: 20px;
  overflow-y: auto;
  border-left: 2px solid var(--accent);
}

.cart-sidebar.open {
  right: 0; /* Se desliza desde la derecha */
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
  color: var(--accent-2);
  font-size: 1.4rem;
}

.close-btn {
  background: none;
  border: none;
  font-size: 1.5rem;
  color: var(--accent-2);
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
  border: 1px solid var(--accent-2);
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
  color: var(--accent-2);
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
  color: var(--accent-2);
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
  border-color: var(--accent-2);
  outline: none;
}

.order-btn {
  width: 100%;
  padding: 15px;
  background-color: var(--accent);
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
  background-color: var(--accent-2);
}

</style>