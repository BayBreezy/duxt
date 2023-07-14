<template>
  <div class="not-prose flex gap-3 rounded-md border p-4">
    <slot name="icon">
      <span v-if="icon" class="flex shrink-0 justify-center">
        <Icon :name="icon" class="h-6 w-6"
      /></span>
    </slot>
    <div class="flex-1">
      <h3 v-if="title" class="mb-1 font-semibold leading-none">{{ title }}</h3>
      <p class="text-sm text-muted-foreground">
        <ContentSlot :use="$slots.default" />
      </p>
    </div>
  </div>
</template>

<script setup lang="ts">
  const props = defineProps<{
    icon?: string;
    title?: string;
  }>();
</script>
