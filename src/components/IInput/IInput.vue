<script setup>
const props = defineProps({
  label: String,
  placeholder: String,
  type: {
    default: 'text',
    type: String,
  },
})

defineOptions({
  inheritAttrs: false,
})
</script>

<template>
  <label class="block w-full">
    <span class="block text-xs font-normal text-content px-4 mb-2">{{ props.label }}</span>
    <input
      class="w-full border border-solid border-content/10 rounded-sm text-sm font-normal text-content px-4.5 py-3.5 focus:outline-accent"
      v-bind="{ ...$props, ...$attrs }"
      @input="changeValue"
    />
  </label>
</template>
