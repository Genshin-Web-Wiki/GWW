<script setup>
import { ref, onMounted } from "vue";
import Characters from "../../public/characters_info.json";
import Premium from "../../public/characters_premium.json";
import { useRoute } from "vue-router";

const characterInfo = ref(null);
const teamPremium = ref(null);
const route = useRoute();
const boolean = ref(false);
onMounted(() => {
  const characterName = route.params.name;

  characterInfo.value = Characters.find(
    (character) => character.name === characterName
  );

  teamPremium.value = Premium.find((character) =>
    characterName.includes(character.name)
  );

  console.log(teamPremium.value);
  boolean.value = true;
});
</script>

<template>
  <div class="p-4">
    <h1>This is an about page</h1>


<p class="block max-w-sm p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700">
    <h2 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white" v-if="boolean">{{ characterInfo.name }}</h2>
    <p class="font-normal text-gray-700 dark:text-gray-400" v-if="boolean">{{ teamPremium.name }}</p>
    </p>
  </div>
</template>

<style lang="scss" scoped></style>
