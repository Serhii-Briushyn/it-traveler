<script setup>
import FavoriteButton from './FavoriteButton.vue'
</script>

<template>
  <li class="flex gap-3.5 pb-5 border-b border-content/10">
    <img
      class="w-[76px] h-[76px] shrink-0 rounded-sm"
      src="../../assets/img/Rectangle.jpg"
      alt="Favorite marker photo"
    />
    <div>
      <div class="flex justify-between items-center mb-2">
        <h2 class="font-medium text-sm tracking-tight text-content">Пункт незламності</h2>
        <div class="flex gap-2">
          <FavoriteButton
            ><svg
              class="stroke-content/50 fill-none w-4 h-4 hover:stroke-accent transition-colors duration-300"
            >
              <use xlink:href="/sprite.svg#icon-edit"></use>
            </svg>
          </FavoriteButton>
          <FavoriteButton>
            <svg
              class="stroke-content/50 fill-none w-4 h-4 hover:stroke-accent transition-colors duration-300"
            >
              <use xlink:href="/sprite.svg#icon-delete"></use>
            </svg>
          </FavoriteButton>
        </div>
      </div>
      <p class="text-xs tracking-tight text-content/50 line-clamp-3">
        Проєкт української влади, який ініціювали у листопаді 2022 року на фоні масованих обстрілів
        критичної інфраструктури з боку Росії під час російсько-української війни.
      </p>
    </div>
  </li>
</template>
