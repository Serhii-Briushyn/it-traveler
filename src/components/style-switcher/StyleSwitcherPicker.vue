<script setup>
import { onMounted, ref, watch } from 'vue'

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
  document.documentElement.style.setProperty('--color-accent-light', `var(${color.light})`)

  localStorage.setItem('selectedColor', color.main)
  localStorage.setItem('selectedLightColor', color.light)
}

onMounted(() => {
  document.documentElement.style.setProperty('--color-accent', `var(${selectedColor.value})`)
  document.documentElement.style.setProperty(
    '--color-accent-light',
    `var(${selectedLightColor.value})`,
  )
})

watch([selectedColor, selectedLightColor], () => {
  document.documentElement.style.setProperty('--color-accent', `var(${selectedColor.value})`)
  document.documentElement.style.setProperty(
    '--color-accent-light',
    `var(${selectedLightColor.value})`,
  )
})
</script>

<template>
  <ul class="grid grid-cols-3 gap-2">
    <li
      v-for="color in colors"
      :key="color.main"
      class="group cursor-pointer rounded-md border border-solid border-gray-700 p-1.5"
      :class="{ 'bg-gray-700': selectedColor === color.main }"
      @click="changeColor(color)"
    >
      <svg
        class="h-8 w-8 transition-all duration-200 ease-in group-hover:scale-110"
        :style="{ fill: `var(${color.main})` }"
      >
        <use xlink:href="/sprite.svg#icon-map-pin"></use>
      </svg>
    </li>
  </ul>
</template>
