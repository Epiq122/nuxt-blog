<template>
  <div>Projects</div>
  <section :if="pending">Loading....</section>
  <section :else-if="error">Something went wrong try again......</section>
  <section :else>Display the repos</section>
</template>

<script setup>
const { error, pending, data } = await useFetch(
  'https://api.github.com/users/epiq122/repos',
);
</script>

<style scoped></style>
