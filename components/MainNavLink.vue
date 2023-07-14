<template>
  <nav class="flex flex-col pl-3">
    <NuxtLink
      exact-active-class="text-primary underline underline-offset-4"
      class="p-2 text-sm text-muted-foreground transition-colors hover:text-primary hover:underline hover:underline-offset-4"
      :to="child._path"
      v-for="(child, i) in links"
    >
      <p class="truncate">
        {{ child.title }}
      </p>
    </NuxtLink>
  </nav>
</template>

<script setup lang="ts">
  defineProps<{
    links?: any[];
  }>();
</script>
