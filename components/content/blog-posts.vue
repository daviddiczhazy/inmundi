<script setup lang="ts">
const { data: docs } = await useAsyncData("documents-list", async () => {
  const allDocs = await queryCollection("docs")
    .where("path", "<>", "/blog")
    .select("path", "title", "description", "meta")
    .all();

  return allDocs.sort((a, b) =>
    (b.meta?.published || "") > (a.meta?.published || "") ? 1 : -1
  );
});

const posts = computed(() => {
  if (!docs.value) return [];

  const result = [];
  let lastyear = null;

  for (const post of docs.value) {
    const year = new Date(post?.meta?.published).getFullYear();

    const dislplayYear = year !== lastyear;

    post.displayYear = dislplayYear;
    post.year = year;
    result.push(post);
    lastyear = year;
  }
  return result;
});
</script>

<template>
  <div class="not-prose font-mono">
    <div
      class="flex items-center space-x-8 py-2 border-b border-gray-200 text-gray-400 text-sm"
    >
      <div>Dátum</div>
      <div>Názov</div>
    </div>
    <NuxtLink v-for="post in posts" :key="post.path" :to="post.path">
      <div
        class="flex items-center space-x-8 py-2 border-b border-gray-200 hover:bg-gray-100 dark:hover:bg-gray-700"
      >
        <div :class="{ 'text-white': !post.displayYear }">
          {{ post.year }}
        </div>
        <div class="uppercase">{{ post.title }}</div>
      </div>
    </NuxtLink>
  </div>
</template>

<style scoped>
.posts {
  margin: 1em 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 1em;
}
</style>
