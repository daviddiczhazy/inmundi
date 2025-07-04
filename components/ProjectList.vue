<script setup lang="ts">
interface Repo {
  id: number;
  name: string;
  html_url: string;
  stargazers_count: number;
  description: string | null;
}

const { error, pending, data } = await useFetch<Repo[]>(
  "https://api.github.com/users/daviddiczhazy/repos"
);

const repos = computed(() => {
  return data.value
    ?.filter((repo) => repo.description)
    .sort((a, b) => b.stargazers_count - a.stargazers_count);
});
</script>

<template>
  <div class="mt-8">
    <h3>Zoznam GIThub projektov:</h3>
  </div>
  <section v-if="pending">Načitavam...</section>
  <section v-else-if="error">Niečo sa pokazilo... skús znova</section>
  <section v-else>
    <ul class="grid grid-cols-1 gap-4 mt-4">
      <li
        v-for="repo in repos"
        :key="repo.id"
        class="border border-gray-200 p-4 rounded-sm hover:bg-gray-100 font-mono"
      >
        <a :href="repo.html_url" target="_blank">
          <div class="flex items-center justify-between">
            <div class="font-semibold">
              {{ repo.name }}
              <p class="text-sm font-light">{{ repo.description }}</p>
            </div>
            <div>{{ repo.stargazers_count }} *</div>
          </div></a
        >
      </li>
    </ul>
  </section>
</template>
