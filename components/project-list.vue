<template>
  <div>Projects</div>
  <section v-if="pending">Loading....</section>
  <section v-else-if="error">Something went wrong try again......</section>
  <section v-else>Display the repos</section>
</template>

<script setup>
const { error, pending, data } = await useFetch(
  'https://api.github.com/users/epiq122/repos',
);
</script>

<style scoped></style>
