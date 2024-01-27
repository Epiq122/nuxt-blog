<template>
  <div>This page is about me</div>
  <div>
    <button @click="enableCustomLayout">Update Layout</button>
  </div>
</template>

<!-- <script>
definePageMeta({
  layout: 'another',
  title: 'About',
});
</script> -->

<script setup>
function enableCustomLayout() {
  setPageLayout('another');
}
</script>

<style scoped></style>
