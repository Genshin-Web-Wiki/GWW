<script setup>
import {
  ref,
  onUpdated,
  watchEffect,
  reactive,
  onMounted,
  computed,
} from "vue";
import Proba from "../components/proba.vue";
import Character from "../components/characterinfo.vue";
const firstJson = ref(null);
const secondJson = ref(null);
const charArray = ref(null);

onMounted(async () => {
  const response1 = await fetch("../../public/characters_info.json");
  const response2 = await fetch("../../public/characters_premium.json");

  firstJson.value = await response1.json();
  secondJson.value = await response2.json();
  console.log("papapapap");
  console.log(firstJson.value);
  console.log(secondJson.value);

  const matching = [];
  firstJson.value.forEach((item) => {
    const otherItem = secondJson.value.find((other) =>
      item.name.includes(other.name)
    );

    if (otherItem) {
      matching.push({
        name: item.name,
        value: item,
        premium: otherItem,
      });
    }
  });
  console.log(matching);
  charArray.value = matching;
});
</script>

<template>
  <Character v-for="character in charArray" :character_info="character" />
</template>
