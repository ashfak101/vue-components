<script setup lang="ts">
import { type HTMLAttributes } from 'vue'
import { cn } from '@/lib/utils'

const props = defineProps<{
  label: string
  class?: HTMLAttributes['class']
}>()
</script>

<template>
  <div :class="cn('sm:col-span-1', props.class)">
    <dt class="text-sm font-medium text-muted-foreground">
      {{ label }}
    </dt>
    <dd class="mt-1 text-sm text-foreground">
      <slot />
    </dd>
  </div>
</template>
