<script setup>
const colorMode = useColorMode();

const modes = ["system", "light", "dark"];

const nextMode = computed(() => {
  const currentIndex = modes.indexOf(colorMode.preference);
  let nextModeIndex = null;
  if (currentIndex + 1 === modes.length) {
    nextModeIndex = 0; // Default to light if not found
  } else {
    nextModeIndex = (currentIndex + 1) % modes.length;
  }
  return modes[nextModeIndex];
});

const toggleMode = () => {
  colorMode.preference = nextMode.value;
};
</script>

<template>
  <button class="cursor-pointer" @click="toggleMode">{{ nextMode }}</button>
</template>
