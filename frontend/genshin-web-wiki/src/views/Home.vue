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
    <h1>Characters</h1>
    <ul>
      <li v-for="character in Characters" :key="character.name">
        <router-link :to="'/' + character.name">{{
          character.name
        }}</router-link>
      </li>
    </ul>
  </div>
</template>
