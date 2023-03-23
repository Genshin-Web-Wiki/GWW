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
  <div class="p-4 flex flex-col">
    <h1>This is an about page</h1>
    <div
      class="block w-full p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700"
    >
      <h2
        class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
        v-if="boolean"
      >
        {{ characterInfo.name }}
      </h2>
    </div>
    <div
      class="block w-full p-6 bg-white border border-gray-200 rounded-lg shadow hover:bg-gray-100 dark:bg-gray-800 dark:border-gray-700 dark:hover:bg-gray-700"
    >
    <h2
        class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"
      >
        Premium Team
      </h2>
      <!-- <p class="font-normal text-gray-700 dark:text-gray-400" v-if="boolean">
        {{ teamPremium.name }}
      </p> -->
      <ul v-if="boolean">
        <li v-for="teammate in teamPremium.premium_team">{{ teammate }}</li>
      </ul>


<div class="relative overflow-x-auto shadow-md sm:rounded-lg" v-if="boolean">
    <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
        <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
            <tr>
                <th scope="col" class="px-6 py-3">
                    Main DPS
                </th>
                <th scope="col" class="px-6 py-3">
                    Support
                </th>
                <th scope="col" class="px-6 py-3">
                    Healer
                </th>
                <th scope="col" class="px-6 py-3">
                    Sub DPS
                </th>
            </tr>
        </thead>
        <tbody>
            <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700 hover:bg-gray-50 dark:hover:bg-gray-600">
                <!-- <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                    Apple MacBook Pro 17"
                </th>
                <td class="px-6 py-4">
                    Silver
                </td>
                <td class="px-6 py-4">
                    Laptop
                </td>
                <td class="px-6 py-4">
                    $2999
                </td>
                <td class="px-6 py-4 text-right">
                    <a href="#" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</a>
                </td> -->
                <td class="px-6 py-4" v-for="teammate in teamPremium.premium_team">{{ teammate }}</td>
            </tr>
            
        </tbody>
    </table>
</div>


    </div>

    

    <router-link
      class="text-gray-900 bg-gradient-to-r from-red-200 via-red-300 to-yellow-200 hover:bg-gradient-to-bl focus:ring-4 focus:outline-none focus:ring-red-100 dark:focus:ring-red-400 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2 max-w-sm"
      :to="'/'"
    >
      Back to Homepage
    </router-link>
  </div>
</template>

<style lang="scss" scoped></style>
