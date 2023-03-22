<template>
  <div>
    <h2>{{ character_info.name }}</h2>
    <p>{{ character_info.value.vision }}</p>
    <p>{{ character_info.premium.name }}</p>
  </div>
</template>

<script setup>
const props = defineProps({
  character_info: Object,
});
</script>

<style lang="scss" scoped></style>
