<template>
  <div class="container mx-auto max-w-4xl">
    <header class="flex justify-between items-center mt-4">
      <div>
        <NuxtLink
          to="/"
          class="text-xl font-bold hover:bg-gray-200 p-2 rounded-sm"
        >
          Diskusné fórum
        </NuxtLink>
      </div>
      <MainMenu />
      <ColorModeSelector />
    </header>

    <main class="p-2 mt-8">
      <slot />
    </main>
  </div>
</template>

<script setup>
useHead({
  // as a string,
  // where `%s` is replaced with the title
  titleTemplate: "%s - Diskusné fórum",
  link: [
    {
      rel: "preconnect",
      href: "https://fonts.googleapis.com",
    },
    {
      rel: "stylesheet",
      href: "https://fonts.googleapis.com/css2?family=Roboto&display=swap",
      crossorigin: "",
    },
  ],
});
</script>

<style>
body {
  font-family: "Roboto", sans-serif;
}
</style>
