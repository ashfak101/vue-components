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

const colsMap = {
  1: 'grid-cols-1',
  2: 'grid-cols-2',
  3: 'grid-cols-3',
  4: 'grid-cols-4',
  5: 'grid-cols-5',
  6: 'grid-cols-6',
  8: 'grid-cols-8',
  10: 'grid-cols-10',
  12: 'grid-cols-12',
  none: 'grid-cols-none',
}

const gapMap = {
  0: 'gap-0',
  1: 'gap-1',
  2: 'gap-2',
  3: 'gap-3',
  4: 'gap-4',
  5: 'gap-5',
  6: 'gap-6',
  8: 'gap-8',
  10: 'gap-10',
  12: 'gap-12',
  16: 'gap-16',
}

const colsClass = computed(() => colsMap[props.cols as keyof typeof colsMap])
const gapClass = computed(() => gapMap[props.gap as keyof typeof gapMap])

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
