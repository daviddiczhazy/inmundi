<template>
  <div>
    <h3>Sme vnutri clanku</h3>
  </div>
</template>
<script setup lang="ts">
const route = useRoute();

// When accessing /posts/1, route.params.id will be 1
console.log(route.params.id);
</script>
