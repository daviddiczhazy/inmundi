<script setup lang="ts">
useSeoMeta({
  title: "Diskusné fórum",
  description: "Blogy a diskusie o rôznych témach",
  ogTitle: "Diskusné fórum",
  ogDescription: "Blogy a diskusie o rôznych témach",
  ogImage: "/og-image.png",
  ogUrl: "https://example.com",
  twitterTitle: "Diskusné fórum",
  twitterDescription: "Blogy a diskusie o rôznych témach",
  twitterImage: "/og-image.png",
  twitterCard: "summary",
});

useHead({
  htmlAttrs: {
    lang: "en",
  },
  link: [
    {
      rel: "icon",
      type: "image/png",
      href: "/favicon.png",
    },
  ],
});
</script>
<template>
  <div>
    <h1>Diskusné fórum</h1>
  </div>
</template>
