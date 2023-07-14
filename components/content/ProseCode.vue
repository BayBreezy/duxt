<template>
  <div class="relative">
    <div class="absolute right-3 top-2 z-10">
      <button
        @click="copy()"
        class="flex h-8 w-8 items-center justify-center rounded bg-background"
      >
        <Icon :name="copied ? 'heroicons:hand-thumb-up' : 'heroicons:clipboard'" class="h-4 w-4" />
      </button>
    </div>
    <slot />
  </div>
</template>

<script setup lang="ts">
  const props = withDefaults(
    defineProps<{
      code?: string;
      language?: string;
      filename?: string;
      highlights?: number[];
      meta?: string;
    }>(),
    {
      code: "",
      language: "vue",
      highlights: () => [],
    }
  );

  const { copy, copied } = useClipboard({
    source: () => props.code,
    legacy: true,
    copiedDuring: 2500,
  });
</script>

<style>
  pre code .line {
    display: block;
    min-height: 1rem;
  }
  pre {
    @apply max-h-[450px];
  }
</style>
