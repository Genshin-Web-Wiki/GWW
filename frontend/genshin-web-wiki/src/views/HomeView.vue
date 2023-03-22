<script setup>
import { ref, onUpdated, watchEffect, reactive } from "vue";
import Proba from "../components/proba.vue";
const response = ref(null);

const fetchData = async () => {
  const data = await fetch("../../public/characters_data.json");
  response.value = await data.json();
  console.log(response.value);
  console.log("patata");
};

fetchData();
</script>

<template>
  <Proba v-for="character in response" :character="character" />
</template>
