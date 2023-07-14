<template>
  <h2 :id="id" class="not-prose">
    <a v-if="id && generate" :href="`#${id}`">
      <slot />
    </a>
    <slot v-else />
  </h2>
</template>

<script setup lang="ts">
  defineProps<{ id?: string }>();
  const heading = 2;
  const { anchorLinks } = useRuntimeConfig().public.content;
  const generate = anchorLinks?.depth >= heading && !anchorLinks?.exclude.includes(heading);
</script>
