<script setup>
defineProps({
  label: String,
  id: String,
  name: String,
  modelValue: [String, Number],
  error: Boolean,
  touched: Boolean,
  errorMessage: String,
  disabled: Boolean,
  required: {
    type: Boolean,
    default: false
  },
  options: {
    type: Array,
    default: () => []
  }
})

const emit = defineEmits(['update:modelValue', 'blur', 'change'])

const getGroupClass = (touched, error) => {
  if (!touched) return ''
  return error ? 'invalid' : 'valid'
}
</script>

<template>
  <div :class="['form-group', getGroupClass(touched, error)]">
    <label v-if="label" :for="id">{{ label }}</label>
    <select
      :id="id"
      :name="name"
      :required="required"
      :value="modelValue"
      @change="e => { emit('update:modelValue', e.target.value); emit('change', e) }"
      @blur="e => emit('blur', e)"
      :disabled="disabled"
    >
      <option 
        v-for="opt in options" 
        :key="opt.value" 
        :value="opt.value" 
        :disabled="opt.disabled"
      >
        {{ opt.label }}
      </option>
    </select>
    <span v-if="touched && error && errorMessage" class="error-message" :id="`${id}Error`">
      {{ errorMessage }}
    </span>
  </div>
</template>
