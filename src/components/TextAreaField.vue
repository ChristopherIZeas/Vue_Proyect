<script setup>
defineProps({
  label: String,
  id: String,
  name: String,
  placeholder: String,
  modelValue: [String, Number],
  error: Boolean,
  touched: Boolean,
  errorMessage: String,
  disabled: Boolean,
  required: {
    type: Boolean,
    default: false
  },
  rows: {
    type: Number,
    default: 4
  }
})

const emit = defineEmits(['update:modelValue', 'blur', 'input'])

const getGroupClass = (touched, error) => {
  if (!touched) return ''
  return error ? 'invalid' : 'valid'
}
</script>

<template>
  <div :class="['form-group', getGroupClass(touched, error)]">
    <label v-if="label" :for="id">{{ label }}</label>
    <textarea
      :id="id"
      :name="name"
      :rows="rows"
      :placeholder="placeholder"
      :required="required"
      :value="modelValue"
      @input="e => { emit('update:modelValue', e.target.value); emit('input', e) }"
      @blur="e => emit('blur', e)"
      :disabled="disabled"
    />
    <span v-if="touched && error && errorMessage" class="error-message" :id="`${id}Error`">
      {{ errorMessage }}
    </span>
  </div>
</template>
