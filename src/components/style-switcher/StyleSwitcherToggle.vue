<script setup>
import { ref, onMounted, watch } from 'vue'

const isDarkMode = ref(localStorage.getItem('theme') === 'dark')

onMounted(() => {
  if (isDarkMode.value) {
    document.documentElement.setAttribute('data-theme', 'dark')
  } else {
    document.documentElement.setAttribute('data-theme', 'light')
  }
})

watch(isDarkMode, (newValue) => {
  if (newValue) {
    document.documentElement.setAttribute('data-theme', 'dark')
    localStorage.setItem('theme', 'dark')
  } else {
    document.documentElement.setAttribute('data-theme', 'light')
    localStorage.setItem('theme', 'light')
  }
})

const setLightTheme = () => {
  isDarkMode.value = false
}

const setDarkTheme = () => {
  isDarkMode.value = true
}
</script>

<template>
  <div class="flex items-center gap-6">
    <button
      @click="setLightTheme"
      class="group basis-1/2 cursor-pointer rounded-md border border-solid border-gray-700 bg-gray-700 p-1.5 dark:bg-inherit"
      title="Light Mode"
    >
      <svg
        class="text-yellow group-hover:text-yellow h-8 w-8 transition-all duration-200 ease-in dark:text-white"
      >
        <use xlink:href="/sprite.svg#uil--moon"></use>
      </svg>
    </button>

    <button
      @click="setDarkTheme"
      class="group basis-1/2 cursor-pointer rounded-md border border-solid border-gray-700 bg-inherit p-1.5 dark:bg-gray-700"
      title="Dark Mode"
    >
      <svg
        class="h-8 w-8 text-white transition-all duration-200 ease-in group-hover:text-blue-500 dark:text-blue-500"
      >
        <use xlink:href="/sprite.svg#uil--sun"></use>
      </svg>
    </button>
  </div>
</template>
