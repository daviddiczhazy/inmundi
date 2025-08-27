<template>
  <NuxtLayout>
    <section>
      <h2 class="text-xl font-bold mb-2">Chyba... {{ error.statusCode }}</h2>
      <p class="text-xl">{{ error.statusMessage }}</p>
    </section>
  </NuxtLayout>
</template>

<script setup>
defineProps({
  error: Object,
});
</script>
