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
  <div>
    <h1>This is an about page</h1>
    <p v-if="boolean">{{ characterInfo.name }}</p>
    <p v-if="boolean">{{ teamPremium.name }}</p>
  </div>
</template>

<style lang="scss" scoped></style>
