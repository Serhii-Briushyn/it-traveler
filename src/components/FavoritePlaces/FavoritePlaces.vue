<script setup>
import FavoritePlace from '../FavoritePlace/FavoritePlace.vue'
import IButton from '../IButton/IButton.vue'
</script>

<template>
  <div>
    <p class="font-normal text-sm tracking-tight text-content/50 mb-4">Added markers</p>
    <ul class="flex flex-col gap-6 mb-10">
      <FavoritePlace v-for="n in 4" :key="n" />
    </ul>

    <IButton variant="primary">Add marker</IButton>
  </div>
</template>
