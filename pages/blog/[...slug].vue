<script lang="ts" setup>
const route = useRoute();
const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection("docs").path(route.path).first();
});

const activeId = ref<string | null>(null);

useHead({
  title: page.value?.title || "Defaultný názov",
  meta: [
    {
      name: "description",
      content: page.value?.description || "Predvolený popis",
    },
  ],
});

onMounted(() => {
  const callback = (entries: IntersectionObserverEntry[]) => {
    for (const entry of entries) {
      if (entry.isIntersecting) {
        activeId.value = entry.target.id;
        break;
      }
    }
  };
  const observer = new IntersectionObserver(callback, {
    root: null,
    threshold: 0.5,
  });
  const elements = document.querySelectorAll("h2, h3");

  for (const el of elements) {
    observer.observe(el);
  }
  onBeforeUnmount(() => {
    for (const element of elements) {
      observer.unobserve(element);
    }
  });
});
</script>

<template>
  <div
    class="prose dark:prose-invert max-w-none prose-h1:text-2xl prose-pre:bg-white dark:prose-pre:bg-gray-800 prose-pre:text-gray-700"
  >
    <template v-if="page">
      <div class="grid grid-cols-6 gap-16 mt-8">
        <div
          :class="{
            'col-span-4': page?.meta?.toc,
            'col-span-6': !page?.meta?.toc,
          }"
        >
          <ContentRenderer :value="page" />
        </div>
        <div v-if="page?.meta?.toc" class="col-span-2 not-prose">
          <aside class="sticky top-8">
            <div class="font-semibold mb-2">Obsah</div>
            <TocLinks :links="page?.body?.toc?.links" :active-id="activeId" />
          </aside>
        </div>
      </div>
    </template>

    <template v-else>
      <div class="empty-page">
        <h1>Stránka sa nenašla - 404</h1>
        <p>Prepáčte! Obsah, ktorý hľadáte, neexistuje.</p>
        <NuxtLink to="/blog">Naspäť na blog</NuxtLink>
      </div>
    </template>
  </div>
</template>
