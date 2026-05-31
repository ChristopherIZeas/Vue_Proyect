<script setup>
defineProps({
  onStartClick: {
    type: Function,
    required: true
  }
})
</script>

<template>
  <section id="hero" class="hero">
    <div class="container hero-container">
      <div class="hero-text">
        <h1>Impulsa tu Presencia <span>Digital</span></h1>
        <p>Diseñamos experiencias web excepcionales que cautivan a tu audiencia y transforman visitantes en clientes.</p>
        <button @click="onStartClick" class="btn btn-primary">Empieza Hoy</button>
      </div>
      <div class="hero-graphic">
        <div class="shape shape-1"></div>
        <div class="shape shape-2"></div>
      </div>
    </div>
  </section>
</template>
