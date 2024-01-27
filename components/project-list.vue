<template>
  <p class="mb-10">Projects</p>
  <section v-if="pending">Loading....</section>

  <section v-else-if="error">Something went wrong try again......</section>

  <section v-else>
    <ul class="grid grid-cols-1 gap-4">
      <li
        v-for="repository in repos"
        :key="repository"
        class="border boder-gray-200 rounded-sm p-4 hover:bg-gray-100 font-mono"
      >
        <a :href="repository.html_url" target="_black">
          <div class="flex items-center justify-between">
            <div class="font-semibold">{{ repository.name }}</div>
            <div>
              <p class="text-sm mt-3">
                {{ formatDate(repository.created_at) }}
              </p>
            </div>
          </div>
          <p class="text-sm">
            {{ repository.description }}
          </p>
        </a>
      </li>
    </ul>
  </section>
</template>

<script setup>
const { error, pending, data } = await useFetch(
  'https://api.github.com/users/epiq122/repos?sort=created&direction=desc',
);
const repos = computed(() => data.value.filter((repo) => repo.description));
const formatDate = (dateString) => {
  const options = { year: 'numeric', month: 'long', day: 'numeric' };
  const date = new Date(dateString);
  return date.toLocaleDateString(undefined, options);
};
</script>

<style scoped></style>
