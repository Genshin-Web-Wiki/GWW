<script setup>
import {
  ref,
  onUpdated,
  watchEffect,
  reactive,
  onMounted,
  computed,
} from "vue";
import Characters from "../../public/characters_info_sorted.json";


</script>

<template>
  <div class="px-4">

    <ul class="mb-8 space-y-4 text-left text-gray-500 dark:text-gray-400">
      <li class="flex items-center space-x-3" v-for="character in Characters" :key="character.name">
        <svg class="flex-shrink-0 w-5 h-5 text-green-500 dark:text-green-400" fill="currentColor" viewBox="0 0 20 20"
          xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd"
            d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
            clip-rule="evenodd"></path>
        </svg>
        <router-link :to="'/' + character.name">{{
          character.name
        }}</router-link>
      </li>
    </ul>
  </div>


  <div class="grid grid-cols-2 md:grid-cols-3 gap-4 px-4">
    <div v-for="character in Characters" :key="character.name">
      <img class="h-auto max-w-full rounded-lg" src="https://flowbite.s3.amazonaws.com/docs/gallery/square/image.jpg"
        alt="">
    </div>

  </div>
</template>
