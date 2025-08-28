<template>
  <ul>
    <li v-for="link in links" :key="link.id">
      <NuxtLink
        :to="{ path: route.path, hash: `#${link.id}` }"
        class="hover:underline"
        :class="{
          'ml-4': props.level,
          'text-green-600': link.id === props.activeId,
        }"
      >
        {{ link.text }}
      </NuxtLink>
      <TocLinks
        v-if="link.children"
        :links="link.children"
        :level="props.level + 1"
        :active-id="props.activeId"
      />
    </li>
  </ul>
</template>
<script setup lang="ts">
type Link = {
  id: string;
  text: string;
  depth: number;
  children?: Link[];
};

interface TocLink {
  links: Link[] | undefined;
  level?: number;
  activeId?: string | null;
}

const route = useRoute();

const props = withDefaults(defineProps<TocLink>(), {
  level: 0,
  activeId: null,
});
</script>
