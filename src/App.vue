<script setup>
import { onMounted, onUnmounted, ref} from 'vue'

const isMobile = ref(false)

const handleResize = () => {
  if (window.innerWidth < 990) {
    isMobile.value = true
  } else {
    isMobile.value = false
  }
}


onMounted(() => {
  handleResize()
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>
<template>
  <div>
    <head>
      <title>Frontend Mentor - Preview Card</title>
      <meta name="description" content="">
    </head>
    <main>
      <div class="card__main">
        <img v-if="isMobile" src="./assets/images/image-product-mobile.jpg" alt="">
        <img v-else src="./assets/images/image-product-desktop.jpg" alt="">
        <div class="info_card">
          <h1>Perfume</h1>
          <h2>Gabrielle Essense Eau De Perfume</h2>
          <p>
            A floral, solar and voluptuous interpretation composed by Olivier Polge, 
            Perfumer-Creator for the House of CHANEL.
          </p>
          <div class="price-container">
            <h4 class="price_discount">$149.99</h4>
            <p class="actual_price">$169.99</p>
          </div>
          <button><span><img src="./assets/images/icon-cart.svg" /></span> Add to Cart</button>
        </div>
      </div>
    </main>
  </div>
</template>
