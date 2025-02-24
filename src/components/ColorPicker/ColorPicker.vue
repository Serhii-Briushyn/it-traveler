<script setup>
import { ref, watchEffect, onMounted, onUnmounted } from 'vue'

const isOpen = ref(false)

const colors = [
  { name: 'Orange', main: '--color-orange', light: '--color-orange-light' },
  { name: 'Blue', main: '--color-blue', light: '--color-blue-light' },
  { name: 'Green', main: '--color-green', light: '--color-green-light' },
  { name: 'Red', main: '--color-red', light: '--color-red-light' },
  { name: 'Purple', main: '--color-purple', light: '--color-purple-light' },
  { name: 'Yellow', main: '--color-yellow', light: '--color-yellow-light' },
]

const selectedColor = ref(localStorage.getItem('selectedColor') || '--color-orange')
const selectedLightColor = ref(localStorage.getItem('selectedLightColor') || '--color-orange-light')

const changeColor = (color) => {
  if (!color) return

  selectedColor.value = color.main
  selectedLightColor.value = color.light

  document.documentElement.style.setProperty('--color-accent', `var(${color.main})`)
  document.documentElement.style.setProperty('--color-background-button', `var(${color.light})`)

  localStorage.setItem('selectedColor', color.main)
  localStorage.setItem('selectedLightColor', color.light)

  isOpen.value = false
}

const clickOutside = (event) => {
  if (!event.target.closest('.color-picker')) {
    isOpen.value = false
  }
}

onMounted(() => {
  document.addEventListener('click', clickOutside)
})

onUnmounted(() => {
  document.removeEventListener('click', clickOutside)
})

watchEffect(() => {
  document.documentElement.style.setProperty('--color-accent', `var(${selectedColor.value})`)
  document.documentElement.style.setProperty(
    '--color-background-button',
    `var(${selectedLightColor.value})`,
  )
})
</script>

<template>
  <div class="absolute top-6 right-6 color-picker">
    <div
      class="w-10 h-10 rounded-full cursor-pointer"
      :style="{ backgroundColor: `var(${selectedColor})` }"
      @click="isOpen = !isOpen"
    ></div>

    <div
      v-if="isOpen"
      class="absolute top-12 left-0 flex flex-col gap-1 transition-all duration-300"
    >
      <div
        v-for="color in colors"
        :key="color.main"
        class="w-10 h-10 rounded-full cursor-pointer transition-all duration-300 hover:scale-105"
        :style="{ backgroundColor: `var(${color.main})` }"
        @click="changeColor(color)"
      ></div>
    </div>
  </div>
</template>
