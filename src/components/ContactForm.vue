<script setup>
import { ref, reactive } from 'vue'
import InputField from './InputField.vue'
import SelectField from './SelectField.vue'
import TextAreaField from './TextAreaField.vue'

const serviceOptions = [
  { value: '', label: 'Selecciona un servicio...', disabled: true },
  { value: 'web', label: 'Desarrollo Web' },
  { value: 'mobile', label: 'Desarrollo Móvil' },
  { value: 'design', label: 'Diseño UI/UX' },
  { value: 'marketing', label: 'Marketing Digital' }
]

const formData = reactive({
  fullName: '',
  email: '',
  service: '',
  message: ''
})

const errors = reactive({
  fullName: false,
  email: false,
  service: false,
  message: false
})

const touched = reactive({
  fullName: false,
  email: false,
  service: false,
  message: false
})

const isSubmitting = ref(false)
const showSuccess = ref(false)

const isEmailValid = (email) => {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
  return re.test(String(email).toLowerCase())
}

const isLengthValid = (value, minLength) => {
  return value.trim().length >= minLength
}

const validateField = (name, value) => {
  switch (name) {
    case 'fullName':
      return !isLengthValid(value, 3)
    case 'email':
      return !isEmailValid(value)
    case 'service':
      return value === ''
    case 'message':
      return !isLengthValid(value, 10)
    default:
      return false
  }
}

const handleChange = (name) => {
  touched[name] = true
  errors[name] = validateField(name, formData[name])
}

const handleBlur = (name) => {
  touched[name] = true
  errors[name] = validateField(name, formData[name])
}

const handleSubmit = () => {
  // Validate all fields
  errors.fullName = validateField('fullName', formData.fullName)
  errors.email = validateField('email', formData.email)
  errors.service = validateField('service', formData.service)
  errors.message = validateField('message', formData.message)

  touched.fullName = true
  touched.email = true
  touched.service = true
  touched.message = true

  const isFormValid = !Object.values(errors).some(err => err)

  if (isFormValid) {
    isSubmitting.value = true

    // Simulate server request (1.5s matching original React/JS timer)
    setTimeout(() => {
      isSubmitting.value = false
      showSuccess.value = true

      // Reset form
      formData.fullName = ''
      formData.email = ''
      formData.service = ''
      formData.message = ''

      touched.fullName = false
      touched.email = false
      touched.service = false
      touched.message = false

      // Hide success message after 1 second (matching original timeout)
      setTimeout(() => {
        showSuccess.value = false
      }, 1000)
    }, 1500)
  }
}
</script>

<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="section-heading">
        <h2>Trabajemos Juntos</h2>
        <p>Completa el formulario y nos pondremos en contacto contigo en breve.</p>
      </div>

      <div class="form-wrapper">
        <form id="contactForm" class="contact-form" @submit.prevent="handleSubmit" novalidate>

          <InputField
            label="Nombre Completo"
            id="fullName"
            name="fullName"
            placeholder="Ej. Juan Pérez"
            required
            v-model="formData.fullName"
            @input="handleChange('fullName')"
            @blur="handleBlur('fullName')"
            :error="errors.fullName"
            :touched="touched.fullName"
            errorMessage="Por favor, ingresa tu nombre (mínimo 3 caracteres)."
            :disabled="isSubmitting"
          />

          <InputField
            type="email"
            label="Correo Electrónico"
            id="email"
            name="email"
            placeholder="ejemplo@correo.com"
            required
            v-model="formData.email"
            @input="handleChange('email')"
            @blur="handleBlur('email')"
            :error="errors.email"
            :touched="touched.email"
            errorMessage="Ingresa un correo electrónico válido."
            :disabled="isSubmitting"
          />

          <SelectField
            label="Servicio de Interés"
            id="service"
            name="service"
            v-model="formData.service"
            @change="handleChange('service')"
            @blur="handleBlur('service')"
            :error="errors.service"
            :touched="touched.service"
            errorMessage="Por favor, selecciona un servicio."
            :disabled="isSubmitting"
            :options="serviceOptions"
          />

          <TextAreaField
            label="Mensaje"
            id="message"
            name="message"
            placeholder="Cuéntanos sobre tu proyecto..."
            required
            v-model="formData.message"
            @input="handleChange('message')"
            @blur="handleBlur('message')"
            :error="errors.message"
            :touched="touched.message"
            errorMessage="El mensaje debe tener al menos 10 caracteres."
            :disabled="isSubmitting"
          />

          <button
            type="submit"
            class="btn btn-submit"
            id="submitBtn"
            :disabled="isSubmitting"
          >
            <span class="btn-text">
              {{ isSubmitting ? 'Enviando...' : 'Enviar Mensaje' }}
            </span>
          </button>

          <div v-if="showSuccess" id="formSuccess" class="form-success">
            ¡Gracias! Tu mensaje ha sido enviado con éxito.
          </div>
        </form>
      </div>
    </div>
  </section>
</template>
