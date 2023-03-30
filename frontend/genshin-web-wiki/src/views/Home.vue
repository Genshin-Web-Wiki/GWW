<script setup>
import {
  ref,
  onUpdated,
  watchEffect,
  reactive,
  onMounted,
  computed,
} from "vue";
import Characters from "../../public/characters_info.json";
import NavBar from "../components/navbar.vue";

const searchName = ref(null);
const charArray = ref(null);
charArray.value = Characters;

const raritySearch = (n) => {
  return Characters.filter((character) => character.rarity === n);
};
const searchByName = (name) => {
  return Characters.filter((character) =>
    character.name.toLowerCase().startsWith(name.toLowerCase())
  );
};

const searchFunction = () => {
  charArray.value = searchByName(searchName.value);
};
</script>

<template>
  <NavBar />
  <div class="px-4 flex flex-row items-center justify-center">
    <label
      for="default-search"
      class="mb-2 text-sm font-medium text-gray-900 sr-only"
      >Search</label
    >
    <div class="relative">
      <div
        class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none"
      >
        <svg
          aria-hidden="true"
          class="w-5 h-5 text-gray-500"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
          ></path>
        </svg>
      </div>
      <input
        @keyup="searchFunction()"
        v-model="searchName"
        type="search"
        id="default-search"
        class="block w-96 p-4 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500"
        placeholder="Search Character by name"
        required
      />
    </div>
  </div>
  <div class="grid grid-cols-2 md:grid-cols-3 gap-4 px-4 py-8">
    <div v-for="character in charArray" :key="character.id">
      <router-link
        :to="'/' + character.id"
        class="flex flex-col justify-center items-center"
      >
        <img
          class="h-auto max-w-full rounded-lg w-28"
          :src="`../../public/images/${character.id}/icon.png`"
          alt=""
        />
        <p class="text-center">{{ character.name }}</p>
      </router-link>
    </div>
  </div>
</template>
