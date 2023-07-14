<template>
  <div class="not-prose mt-10 grid gap-7 border-t py-10 sm:grid-cols-2">
    <NuxtLink
      :to="prev ? prev._path : '#'"
      class="group rounded-lg border p-4 transition-colors hover:border-primary/50 lg:p-6"
      v-if="prev"
    >
      <div
        class="flex h-10 w-10 items-center justify-center rounded-full border bg-background transition group-hover:border-primary/50 group-hover:bg-primary"
      >
        <Icon name="heroicons:arrow-left" class="h-4 w-4 group-hover:text-background" />
      </div>
      <p class="mt-5 font-semibold">{{ prev.title }}</p>
      <p class="mt-1 text-sm text-muted-foreground">{{ prev.description }}</p>
    </NuxtLink>
    <span v-else>{{ "" }}</span>
    <NuxtLink
      :to="next ? next._path : '#'"
      class="group rounded-lg border p-4 text-right transition-colors hover:border-primary/50 lg:p-6"
      v-if="next"
    >
      <div
        class="ml-auto flex h-10 w-10 items-center justify-center rounded-full border bg-background transition group-hover:border-primary/50 group-hover:bg-primary"
      >
        <Icon name="heroicons:arrow-right" class="h-4 w-4 group-hover:text-background" />
      </div>
      <p class="mt-5 font-semibold">{{ next.title }}</p>
      <p class="mt-1 text-sm text-muted-foreground">{{ next.description }}</p>
    </NuxtLink>
    <span v-else>{{ "" }}</span>
  </div>
</template>

<script setup lang="ts">
  const { next, prev } = useContent();
</script>
