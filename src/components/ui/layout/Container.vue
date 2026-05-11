<script setup lang="ts">
import { type HTMLAttributes } from 'vue'
import { cn } from '@/lib/utils'

interface Props {
  class?: HTMLAttributes['class']
  fluid?: boolean
}

const props = defineProps<Props>()
</script>

<template>
  <div
    :class="cn(
      'mx-auto w-full px-4',
      fluid ? 'max-w-none' : 'max-w-7xl sm:px-6 lg:px-8',
      props.class
    )"
  >
    <slot />
  </div>
</template>
