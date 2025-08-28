<template>
  <div class="container mx-auto max-w-4xl">
    <header class="md:flex md:justify-around items-center flex-col mt-4">
      <!-- <div>
        <NuxtLink
          to="/"
          class="text-xl font-bold hover:bg-gray-200 p-2 rounded-sm"
        >
          Diskusné fórum
        </NuxtLink>
      </div> -->
      <MainMenu />
      <div class="w-4xl title-double" />
      <h1
        class="text-2xl md:text-4xl font-semibold font-serif uppercase text-gray-700 text-center page-title"
      >
        INMUNDI spravodajský portál
      </h1>
      <div class="w-4xl title-double" />
      <!-- <ColorModeSelector /> -->
    </header>

    <main class="flex justify-around items-center p-2 mt-8">
      <slot />
    </main>
    <footer>
      <div class="text-center text-gray-500 text-sm py-4">
        &copy; {{ new Date().getFullYear() }} INMUNDI. Všetky práva vyhradené.
      </div>
    </footer>
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

.page-title {
  margin: 1rem 0;
  padding: 2rem 0;
}
.title-double {
  border-top: 2px solid #000;
  border-bottom: 2px solid #000;
  min-height: 0.35rem;
}
</style>
