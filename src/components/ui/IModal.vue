<script setup>
import { onMounted, onUnmounted } from 'vue'

const emit = defineEmits(['close'])

const handleKeydown = (event) => {
  if (event.key === 'Escape') {
    emit('close')
  }
}

onMounted(() => {
  document.body.style.overflow = 'hidden'
  window.addEventListener('keydown', handleKeydown)
})

onUnmounted(() => {
  document.body.style.overflow = ''
  window.removeEventListener('keydown', handleKeydown)
})
</script>

<template>
  <Teleport to="body">
    <div
      class="fixed inset-0 z-100 overflow-auto bg-black/50 text-black dark:text-white"
      @click.self="emit('close')"
    >
      <div
        class="dark:bg-theme-dark-light relative top-1/2 left-1/2 inline-flex -translate-x-1/2 -translate-y-1/2 rounded-2xl bg-white transition-all duration-300"
      >
        <button
          class="absolute top-6 right-6 h-7 w-7 cursor-pointer transition-all duration-200 ease-in hover:scale-125"
          @click="emit('close')"
        >
          <svg class="h-full w-full stroke-black dark:stroke-white">
            <use xlink:href="/sprite.svg#icon-close"></use>
          </svg>
        </button>
        <slot></slot>
      </div>
    </div>
  </Teleport>
</template>
