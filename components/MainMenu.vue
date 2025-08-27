<template>
  <nav class="font-mono">
    <ul class="flex space-x-4">
      <li>
        <NuxtLink to="/" class="hover:bg-gray-200 p-2 rounded-sm"
          >Domov</NuxtLink
        >
      </li>
      <li>
        <NuxtLink to="/blog/domace" class="hover:bg-gray-200 p-2 rounded-sm"
          >Domáce</NuxtLink
        >
      </li>
      <li>
        <NuxtLink to="/blog/zahranicne" class="hover:bg-gray-200 p-2 rounded-sm"
          >Zahraničné</NuxtLink
        >
      </li>

      <li>
        <NuxtLink
          to="/blog/technologie"
          class="hover:bg-gray-200 p-2 rounded-sm"
          >Technológie</NuxtLink
        >
      </li>

      <li>
        <NuxtLink to="/about" class="hover:bg-gray-200 p-2 rounded-sm"
          >O projekte</NuxtLink
        >
      </li>
    </ul>
  </nav>
</template>
