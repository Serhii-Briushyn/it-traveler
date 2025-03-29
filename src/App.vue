<script setup>
import LoginForm from 'components/auth/LoginForm.vue'
import RegistrationForm from 'components/auth/RegistrationForm.vue'
// import FavoritePlaces from 'components/favorite/FavoritePlaces.vue'
import StyleSwitcher from 'components/style-switcher/StyleSwitcher.vue'
import IModal from 'components/ui/IModal.vue'
import { ref } from 'vue'
// import HomePage from 'views/HomePage.vue'
const isOpen = ref(false)

const openModal = () => {
  isOpen.value = true
}

const closeModal = () => {
  isOpen.value = false
}
</script>

<template>
  <main
    class="desktop:justify-center desktop:flex-row bg-theme-gray dark:bg-theme-dark font-display relative flex min-h-screen flex-col items-center justify-start text-black dark:text-white"
  >
    <!-- <HomePage /> -->
    <!-- <div class="w-[379px] px-6 py-7">
      <FavoritePlaces />
    </div> -->
    <button @click="openModal">Click me</button>
    <RegistrationForm @submit="console.log" />
    <LoginForm @submit="console.log" />
    <IModal v-if="isOpen" @close="closeModal"><RegistrationForm @submit="console.log" /></IModal>
    <StyleSwitcher />
  </main>
</template>
