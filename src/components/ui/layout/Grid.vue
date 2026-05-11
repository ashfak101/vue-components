<script setup lang="ts">
import { type HTMLAttributes, computed } from 'vue'
import { cn } from '@/lib/utils'

interface Props {
  class?: HTMLAttributes['class']
  cols?: 1 | 2 | 3 | 4 | 5 | 6 | 8 | 10 | 12 | 'none'
  gap?: 0 | 1 | 2 | 3 | 4 | 5 | 6 | 8 | 10 | 12 | 16
  align?: 'start' | 'center' | 'end' | 'stretch'
}

const props = withDefaults(defineProps<Props>(), {
  cols: 1,
  gap: 4,
  align: 'stretch',
})

const colsClass = computed(() => {
  if (props.cols === 'none') return 'grid-cols-none'
  return `grid-cols-${props.cols}`
})
const gapClass = computed(() => `gap-${props.gap}`)

const alignClasses = {
  start: 'items-start',
  center: 'items-center',
  end: 'items-end',
  stretch: 'items-stretch',
}
</script>

<template>
  <div
    :class="cn(
      'grid',
      colsClass,
      gapClass,
      alignClasses[align],
      props.class
    )"
  >
    <slot />
  </div>
</template>
