<script setup>
import IButton from 'components/ui/IButton.vue'
</script>

<template>
  <section
    class="desktop:flex-row dark:bg-theme-dark desktop:max-h-page-height desktop:h-screen container flex flex-col overflow-hidden bg-white"
  >
    <div
      class="bg-accent dark:bg-theme-dark-light tablet:p-24 flex basis-1/2 items-center justify-center px-8 py-16"
    >
      <div class="text-center text-white">
        <img class="mb-6 inline" src="../assets/img/map-pin.svg" alt="Map pin" />
        <h1 class="mb-7 text-4xl font-bold">IT traveler</h1>
        <p class="mb-11 text-lg tracking-tight">
          A simple and convenient web application that will allow you to mark your favorite places,
          as well as those you would really like to visit. So don't hesitate and try it for
          yourself.
        </p>
        <IButton variant="primary">Get started</IButton>
      </div>
    </div>
    <div class="basis-1/2">
      <img
        class="h-auto w-full object-cover object-bottom"
        src="../assets/img/static-map.png"
        alt="Map image"
      />
    </div>
  </section>
</template>
