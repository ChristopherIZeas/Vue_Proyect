<script setup>
defineProps({
  currentView: {
    type: String,
    required: true
  }
})

const emit = defineEmits(['update:view'])

const handleNavigation = (targetId) => {
  if (targetId === 'styleguide') {
    emit('update:view', 'styleguide')
    window.scrollTo({ top: 0, behavior: 'smooth' })
  } else {
    emit('update:view', 'landing')
    setTimeout(() => {
      const element = document.getElementById(targetId)
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' })
      }
    }, 100)
  }
}
</script>

<template>
  <header class="header">
    <div class="container header-content">
      <button 
        @click="handleNavigation('hero')" 
        class="logo" 
        style="background: none; border: none; cursor: pointer; font-family: inherit; padding: 0;"
      >
        Nexus<span>Tech</span>
      </button>
      <nav class="nav">
        <ul class="nav-list">
          <li>
            <button 
              @click="handleNavigation('hero')" 
              :class="{ active: currentView === 'landing' }"
            >
              Inicio
            </button>
          </li>
          <li>
            <button 
              @click="handleNavigation('contact')"
            >
              Contacto
            </button>
          </li>
          <li>
            <button 
              @click="handleNavigation('styleguide')" 
              :class="{ active: currentView === 'styleguide' }"
            >
              Estandarización
            </button>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>
