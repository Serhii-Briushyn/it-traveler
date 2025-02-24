<script setup>
import IButton from '@/components/IButton/IButton.vue'
</script>

<template>
  <main class="flex h-screen">
    <section class="flex-1 flex justify-center items-center bg-accent">
      <div class="text-white text-center max-w-[570px]">
        <img class="inline mb-6" src="../assets/img/map-pin.svg" alt="Map pin" />
        <h1 class="font-bold text-4xl mb-7">IT traveler</h1>
        <p class="text-lg tracking-tight mb-11">
          A simple and convenient web application that will allow you to mark your favorite places,
          as well as those you would really like to visit. So don't hesitate and try it for
          yourself.
        </p>
        <IButton variant="secondary">Get started</IButton>
      </div>
    </section>
    <section class="flex-1">
      <img class="h-full object-cover" src="../assets/img/static-map.png" alt="Map image" />
    </section>
  </main>
</template>
