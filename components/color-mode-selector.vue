<template>
  <div class="flex space-x-2 items-center">
    <p class="text-gray-500 text-xs">Change to {{ nextMode }}</p>
    <button
      @click="toggleColorMode"
      class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-500"
    >
      {{ nextModeIcon }}
    </button>
  </div>
</template>

<script setup>
const showNextModelLabel = ref(false);
const colorMode = useColorMode();

const modes = ['system', 'light', 'dark'];

const nextModeIcons = {
  system: '🌓',
  light: '🌕',
  dark: '🌑',
};

const nextMode = computed(() => {
  const currentMode = modes.indexOf(colorMode.preference);
  const nextMode = (currentMode + 1) % modes.length;
  return modes[nextMode];
});

const toggleColorMode = () => {
  colorMode.preference = nextMode.value;
};

const nextModeIcon = computed(() => nextModeIcons[nextMode.value]);
</script>

<style lang="scss" scoped></style>
