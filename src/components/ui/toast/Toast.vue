<script setup lang="ts">
import { type HTMLAttributes } from 'vue'
import { cn } from '@/lib/utils'

const props = defineProps<{
  class?: HTMLAttributes['class']
  title?: string
  description?: string
}>()
</script>

<template>
  <div
    :class="cn(
      'pointer-events-auto relative flex w-full items-center justify-between space-x-4 overflow-hidden rounded-md border p-6 pr-8 shadow-lg transition-all bg-background text-foreground',
      props.class
    )"
  >
    <div class="grid gap-1">
      <div v-if="title" class="text-sm font-semibold">
        {{ title }}
      </div>
      <div v-if="description" class="text-sm opacity-90">
        {{ description }}
      </div>
    </div>
    <slot />
  </div>
</template>
