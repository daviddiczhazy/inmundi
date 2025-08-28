<template>
  <nav class="font-mono uppercase mb-2">
    <ul class="mb-2 md:flex menu-separator justify-center">
      <li>
        <NuxtLink to="/" class="hover:bg-gray-200 p-2 mx-2 rounded-sm"
          >Domov</NuxtLink
        >
      </li>
      <li>
        <NuxtLink
          to="/blog/domace"
          class="hover:bg-gray-200 p-2 mx-2 rounded-sm"
          >Domáce</NuxtLink
        >
      </li>
      <li>
        <NuxtLink
          to="/blog/zahranicne"
          class="hover:bg-gray-200 p-2 mx-2 rounded-sm"
          >Zahraničné</NuxtLink
        >
      </li>

      <li>
        <NuxtLink
          to="/blog/technologie"
          class="hover:bg-gray-200 p-2 mx-2 rounded-sm"
          >Technológie</NuxtLink
        >
      </li>

      <li>
        <NuxtLink to="/about" class="hover:bg-gray-200 p-2 mx-2 rounded-sm"
          >O projekte</NuxtLink
        >
      </li>
    </ul>
  </nav>
</template>

<style scoped>
@media screen and (min-width: 768px) {
  .menu-separator li {
    border-right: 2px solid #ccc;
  }
  .menu-separator li:last-child {
    border-right: none;
  }
}

@media screen and (max-width: 767px) {
  .menu-separator li {
    border-bottom: 2px solid #ccc;
    margin: 1rem 0;
    display: block;
    text-align: center;
  }
  .menu-separator li:last-child {
    border-bottom: none;
  }
}
</style>
