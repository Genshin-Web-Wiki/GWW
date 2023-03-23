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

// const firstJson = ref(null);
// const secondJson = ref(null);
// const charArray = ref(null);

// onMounted(async () => {
//   const response1 = await fetch("../../characters_info.json");
//   const response2 = await fetch("../../characters_premium.json");

//   firstJson.value = await response1.json();
//   secondJson.value = await response2.json();
//   console.log("papapapap");
//   console.log(firstJson.value);
//   console.log(secondJson.value);

//   const matching = [];
//   firstJson.value.forEach((item) => {
//     const otherItem = secondJson.value.find((other) =>
//       item.name.includes(other.name)
//     );

//     if (otherItem) {
//       matching.push({
//         name: item.name,
//         value: item,
//         premium: otherItem,
//       });
//     }
//   });
//   console.log(matching);
//   charArray.value = matching;
// });
</script>

<template>
  <div>

<ul class="mb-8 space-y-4 text-left text-gray-500 dark:text-gray-400">
    <li class="flex items-center space-x-3" v-for="character in Characters" :key="character.name">
      <svg class="flex-shrink-0 w-5 h-5 text-green-500 dark:text-green-400" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path></svg>
        <router-link :to="'/' + character.name">{{
          character.name
        }}</router-link>
      </li>
</ul>

  </div>
  <div class="p-4">
    <h1 class="text-teal-500 text-2xl">Characters</h1>
    <ul class="list-disc">
      <li v-for="character in Characters" :key="character.name">
        <router-link :to="'/' + character.name">{{
          character.name
        }}</router-link>
      </li>
    </ul>
  </div>
</template>
