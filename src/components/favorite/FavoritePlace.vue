<script setup>
import FavoriteButton from './FavoriteButton.vue'
</script>

<template>
  <li class="flex gap-3.5 border-b border-black/10 pb-5">
    <img
      class="h-[76px] w-[76px] shrink-0 rounded-sm"
      src="../../assets/img/Rectangle.jpg"
      alt="Favorite marker photo"
    />
    <div>
      <div class="mb-2 flex items-center justify-between">
        <h2 class="text-sm font-medium tracking-tight">Пункт незламності</h2>
        <div class="flex gap-2">
          <FavoriteButton
            ><svg
              class="group-hover:stroke-accent h-4 w-4 fill-none stroke-black/50 transition-colors duration-200 ease-in"
            >
              <use xlink:href="/sprite.svg#icon-edit"></use>
            </svg>
          </FavoriteButton>
          <FavoriteButton>
            <svg
              class="group-hover:stroke-accent h-4 w-4 fill-none stroke-black/50 transition-colors duration-200 ease-in"
            >
              <use xlink:href="/sprite.svg#icon-delete"></use>
            </svg>
          </FavoriteButton>
        </div>
      </div>
      <p class="line-clamp-3 text-xs tracking-tight text-black/50">
        Проєкт української влади, який ініціювали у листопаді 2022 року на фоні масованих обстрілів
        критичної інфраструктури з боку Росії під час російсько-української війни.
      </p>
    </div>
  </li>
</template>
