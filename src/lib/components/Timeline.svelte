<!-- Timeline.svelte -->
<script lang="ts">
  import { Circle } from "@lucide/svelte";
  import type { Component } from "svelte";

  let { items, title, TitleIcon } = $props<{
    items: Array<{ label: string; date: string; desc?: string }>;
    title: string;
    TitleIcon: Component;
  }>();
</script>

<div class="space-y-8">
  <div class="relative">
    <div class="absolute left-5 h-full w-px bg-border top-10"></div>
    <div class="flex items-center gap-4">
      <div
        class="flex h-10 w-10 items-center justify-center rounded-full bg-primary"
      >
        <TitleIcon class="text-primary-foreground" />
      </div>
      <h2 class="text-2xl font-semibold">{title}</h2>
    </div>
  </div>

  <ol class="relative border-l border-border ml-5">
    {#each items as item, index (item.label)}
      <li class="mb-8 ml-6 last:mb-0">
        <div
          class="absolute -left-3 flex h-6 w-6 items-center justify-center rounded-full bg-primary"
        >
          <Circle class="h-2 w-2 text-background fill-background" />
        </div>

        <div class="space-y-1">
          <h3 class="text-lg font-medium">{item.label}</h3>
          <time class="block text-sm text-muted-foreground">{item.date}</time>
          {#if item.desc}
            <p class="text-sm text-muted-foreground">
              {@html item.desc}
            </p>
          {/if}
        </div>
      </li>
    {/each}
  </ol>
</div>
