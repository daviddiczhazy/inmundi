<script lang="ts" setup>
const route = useRoute();
const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection("docs").path(route.path).first();
});

console.log("Current page>", page?.value);

useHead({
  title: page.value?.title || "Defaultný názov",
  meta: [
    {
      name: "description",
      content: page.value?.description || "Predvolený popis",
    },
  ],
});
</script>

<template>
  <div
    class="prose dark:prose-invert max-w-none prose-h1:text-2xl prose-pre:bg-white dark:prose-pre:bg-gray-800 prose-pre:text-gray-700"
  >
    <ContentRenderer v-if="page" :value="page" />
  </div>
</template>
