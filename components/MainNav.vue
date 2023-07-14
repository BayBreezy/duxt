<template>
  <div class="space-y-5">
    <div v-for="(item, i) in navigation" :key="i" class="space-y-3">
      <p class="text-sm font-semibold">{{ item.title }}</p>
      <MainNavLink :links="item.children" />
    </div>
  </div>
</template>

<script setup lang="ts">
  const { navigation } = useContent();
</script>
