<script setup>
import { defineProps, computed } from 'vue'

const props = defineProps({
  variant: {
    default: 'primary',
    type: String,
    validator: (value) => ['primary', 'gradient'].includes(value),
  },
})

const buttonClass = computed(() => {
  return props.variant === 'gradient'
    ? 'w-full bg-gradient-to-r from-accent-light to-accent'
    : 'w-48 bg-accent-light'
})
</script>

<template>
  <button
    class="h-14 cursor-pointer rounded-xl text-base/snug font-bold tracking-tight text-white transition-all duration-200 ease-in hover:scale-105 hover:shadow-[0_4px_10px_rgba(0,0,0,0.3)]"
    :class="buttonClass"
  >
    <slot></slot>
  </button>
</template>
