<script setup lang="ts">
import { type HTMLAttributes } from 'vue'
import { cn } from '@/lib/utils'

const props = defineProps<{
  class?: HTMLAttributes['class']
}>()
</script>

<template>
  <dl :class="cn('grid grid-cols-1 gap-x-4 gap-y-6 sm:grid-cols-2', props.class)">
    <slot />
  </dl>
</template>
