<script setup lang="ts">
import { type HTMLAttributes, computed } from 'vue'
import { cn } from '@/lib/utils'

interface Props {
  class?: HTMLAttributes['class']
  direction?: 'row' | 'col'
  gap?: 0 | 1 | 2 | 3 | 4 | 5 | 6 | 8 | 10 | 12 | 16
  align?: 'start' | 'center' | 'end' | 'baseline' | 'stretch'
  justify?: 'start' | 'center' | 'end' | 'between' | 'around' | 'evenly'
}

const props = withDefaults(defineProps<Props>(), {
  direction: 'col',
  gap: 4,
  align: 'stretch',
  justify: 'start',
})

const directionClass = computed(() => props.direction === 'row' ? 'flex-row' : 'flex-col')
const gapClass = computed(() => `gap-${props.gap}`)

const alignClasses = {
  start: 'items-start',
  center: 'items-center',
  end: 'items-end',
  baseline: 'items-baseline',
  stretch: 'items-stretch',
}

const justifyClasses = {
  start: 'justify-start',
  center: 'justify-center',
  end: 'justify-end',
  between: 'justify-between',
  around: 'justify-around',
  evenly: 'justify-evenly',
}
</script>

<template>
  <div
    :class="cn(
      'flex',
      directionClass,
      gapClass,
      alignClasses[align],
      justifyClasses[justify],
      props.class
    )"
  >
    <slot />
  </div>
</template>
