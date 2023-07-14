<template>
  <div>
    <!-- Mobile drawer -->
    <MobileDrawer v-model="isOpen" />
    <!-- Header -->
    <header class="sticky top-0 z-20 border-b bg-background/80 backdrop-blur">
      <div class="container flex h-16 items-center justify-between">
        <div class="flex items-center gap-3">
          <!-- Button used to show menu on mobile -->
          <button
            @click="isOpen = true"
            class="flex h-9 w-9 items-center justify-center rounded-full border bg-background lg:hidden"
          >
            <Icon name="heroicons:bars-2" class="h-5 w-5" />
          </button>
          <NuxtLink
            class="flex items-center gap-2 text-xl font-bold text-primary"
            to="/getting-started"
            ><img src="/icon.png" class="hidden h-6 w-6 rounded object-contain lg:block" />
            Duxt</NuxtLink
          >
        </div>
        <!-- Button used to switch color mode -->
        <div class="felx items-center">
          <button
            @click="toggleTheme()"
            class="flex h-9 w-9 items-center justify-center rounded-full border bg-background"
          >
            <Icon name="heroicons:sun" class="h-5 w-5" />
          </button>
        </div>
      </div>
    </header>
    <div class="container gap-7 lg:grid lg:grid-cols-12">
      <!-- Sidebar -->
      <aside
        class="hidden overflow-y-auto border-r pb-8 pt-5 lg:sticky lg:top-[65px] lg:col-span-2 lg:block lg:h-[calc(100vh-65px)]"
      >
        <MainNav />
      </aside>
      <!-- Main content -->
      <main class="lg:col-span-10 lg:grid lg:grid-cols-12 lg:gap-5">
        <div
          class="prose prose-slate max-w-none px-3 dark:prose-invert prose-headings:scroll-mt-20 prose-code:before:content-[''] prose-code:after:content-[''] prose-pre:bg-muted lg:col-span-9 lg:px-5"
        >
          <!-- Show info about the page at the top -->
          <PageIntro />
          <slot />
          <!-- Show next/prev links at the bottom -->
          <NextPrev />
        </div>
        <!-- Table of contents -->
        <div v-if="toc && toc.links && toc.links.length" class="hidden lg:col-span-3 lg:block">
          <div class="sticky top-16 overflow-y-auto pb-8 pt-5 lg:h-[calc(100vh-65px)]">
            <p class="text-sm font-semibold">Table of contents</p>

            <nav class="mt-3 flex flex-col pl-2 text-sm">
              <NuxtLink
                class="p-1.5 text-muted-foreground transition hover:text-primary hover:underline hover:underline-offset-4"
                :to="`#${l.id}`"
                v-for="(l, i) in toc.links"
                :key="i"
              >
                {{ l.text }}
              </NuxtLink>
            </nav>
          </div>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
  const { toc } = useContent();
  // Color mode
  const mode = useColorMode();
  // Toggle color mode
  const toggleTheme = () => {
    mode.value = mode.value === "light" ? "dark" : "light";
  };
  // Mobile drawer state
  const isOpen = ref(false);
</script>
