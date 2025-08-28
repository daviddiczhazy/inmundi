<script lang="ts" setup>
useHead({
  title: "Domov",
});

const route = useRoute();
const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection("docs").path(route.path).first();
});
</script>

<template>
  <article class="prose max-w-none">
    <ContentRenderer v-if="page" :value="page" />
  </article>
</template>
