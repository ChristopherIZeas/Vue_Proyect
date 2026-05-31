<script setup>
import { ref } from 'vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import ContactForm from './components/ContactForm.vue'
import StyleGuide from './components/StyleGuide.vue'
import Footer from './components/Footer.vue'

const view = ref('landing')

const handleScrollToContact = () => {
  const contactSection = document.getElementById('contact')
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <Header :currentView="view" @update:view="v => view = v" />

  <main>
    <template v-if="view === 'landing'">
      <Hero :onStartClick="handleScrollToContact" />
      <ContactForm />
    </template>
    <template v-else>
      <StyleGuide />
    </template>
  </main>

  <Footer />
</template>

<style scoped></style>
