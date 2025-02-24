<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  variant: {
    default: 'primary',
    type: String,
    validator: (value) => ['primary', 'secondary'].includes(value),
  },
})

const buttonClass =
  props.variant === 'primary'
    ? 'w-full border-2 border-transparent hover:border-accent'
    : 'w-48 border-none'
</script>

<template>
  <button
    class="bg-background-button rounded-xl h-14 text-white font-bold text-base/snug tracking-tight cursor-pointer transition-all duration-300 ease-in-out hover:bg-white hover:text-accent active:scale-95"
    :class="buttonClass"
  >
    <slot></slot>
  </button>
</template>
