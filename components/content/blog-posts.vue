<script setup lang="ts">
interface TocLink {
  category?: string;
}

const props = withDefaults(defineProps<TocLink>(), {
  category: "",
});

const { data: docs } = await useAsyncData("documents-list", async () => {
  const allDocs = await queryCollection("docs")
    .where("path", "LIKE", `/blog/%`)
    .where("path", "<>", "/blog")
    .where("path", "<>", "/blog/domace")
    .where("path", "<>", "/blog/technologie")
    .where("path", "<>", "/blog/zahranicne")
    .select("path", "title", "description", "meta")
    .all();

  return allDocs.sort((a, b) =>
    (b.meta?.published || "") > (a.meta?.published || "") ? 1 : -1
  );
});

console.log("DOCS: ", docs.value);

const posts = computed(() => {
  if (!docs.value) return [];

  const result = [];
  let lastyear = null;
  const blogs = docs.value.filter((post) =>
    post.path.includes(`blog/${props.category}`)
  );

  for (const post of blogs) {
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
  <slot :posts="posts">
    <div class="not-prose font-mono">
      <div
        class="flex justify-between space-x-8 py-2 border-b border-gray-200 text-gray-400 text-sm"
      >
        <div class="flex items-center space-x-8">
          <div>Dátum</div>
          <div>Názov</div>
        </div>
        <div>Autor</div>
      </div>
      <NuxtLink v-for="post in posts" :key="post.path" :to="post.path">
        <div
          class="flex justify-between group border-b border-gray-200 hover:bg-gray-100 dark:hover:bg-gray-700 px-2"
        >
          <div class="flex items-center space-x-8 py-2">
            <div
              :class="{
                'text-white group-hover:text-gray-100': !post.displayYear,
              }"
            >
              {{ post.year }}
            </div>
            <div>
              <div class="uppercase font-bold">{{ post.title }}</div>
              <div class="text-gray-500 italic">{{ post.description }}</div>
            </div>
          </div>

          <div class="flex items-center py-2">
            {{ post.meta?.Author ?? "Redakcia" }}
          </div>
        </div>
      </NuxtLink>
    </div>
  </slot>
</template>

<style scoped>
.posts {
  margin: 1em 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 1em;
}
</style>
