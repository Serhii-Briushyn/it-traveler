<script setup>
import IButton from 'components/ui/IButton.vue'
import FavoritePlace from './FavoritePlace.vue'
</script>

<template>
  <div>
    <p class="mb-4 text-sm font-normal tracking-tight text-black/50">Added markers</p>
    <ul class="mb-10 flex flex-col gap-6">
      <FavoritePlace v-for="n in 4" :key="n" />
    </ul>

    <IButton variant="gradient">Add marker</IButton>
  </div>
</template>
