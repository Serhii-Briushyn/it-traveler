<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'
import StyleSwitcherPicker from './StyleSwitcherPicker.vue'
import StyleSwitcherToggle from './StyleSwitcherToggle.vue'

const isOpen = ref(false)
const menuRef = ref<HTMLElement | null>(null)

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const closeMenu = () => {
  if (isOpen.value) {
    isOpen.value = false
  }
}

const handleClickOutside = (event) => {
  if (menuRef.value && !menuRef.value.contains(event.target)) {
    closeMenu()
  }
}

onMounted(() => {
  document.addEventListener('mousedown', handleClickOutside)
})

onUnmounted(() => {
  document.removeEventListener('mousedown', handleClickOutside)
})
</script>

<template>
  <div
    ref="menuRef"
    @keydown.esc="closeMenu"
    class="fixed top-80 right-0 z-50 flex -translate-y-1/2 transition-transform duration-500 ease-in"
    :class="isOpen ? 'translate-x-0' : 'translate-x-[13rem]'"
  >
    <button
      @click="toggleMenu"
      class="group bg-theme-dark-light flex h-max cursor-pointer items-center justify-center rounded-l-xl px-1.5 py-3"
      title="Settings"
    >
      <svg class="h-7 w-7 text-white group-hover:animate-spin">
        <use xlink:href="/sprite.svg#uil--setting"></use>
      </svg>
    </button>

    <div class="bg-theme-dark-light w-52 rounded-bl-xl p-4 text-white">
      <h2 class="mb-2 text-center text-base font-bold">Theme Mode</h2>
      <div class="flex flex-col items-center gap-4">
        <StyleSwitcherToggle />
        <StyleSwitcherPicker />
      </div>
    </div>
  </div>
</template>
