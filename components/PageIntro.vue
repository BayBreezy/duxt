<template>
  <div class="mb-7 border-b pt-7">
    <span class="text-sm text-primary">{{ useStartCase(page?._dir?.title || page?._dir) }}</span>
    <h1 class="my-3" v-if="page?.title">{{ page?.title }}</h1>
    <p class="text-muted-foreground lg:text-lg" v-if="page?.description">{{ page?.description }}</p>
  </div>
</template>

<script setup lang="ts">
  const { page } = useContent();
</script>
