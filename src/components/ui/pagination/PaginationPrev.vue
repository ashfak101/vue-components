<script setup lang="ts">
import { type HTMLAttributes, computed } from 'vue'
import { PaginationPrev, type PaginationPrevProps } from 'radix-vue'
import { ChevronLeft } from 'lucide-vue-next'
import {
  Button,
} from '@/components/ui/button'
import { cn } from '@/lib/utils'

const props = defineProps<PaginationPrevProps & { class?: HTMLAttributes['class'] }>()

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props

  return delegated
})
</script>

<template>
  <PaginationPrev v-bind="delegatedProps">
    <Button
      :class="cn('gap-1 px-2.5', props.class)"
      variant="outline"
    >
      <slot>
        <ChevronLeft class="h-4 w-4" />
        <span>Previous</span>
      </slot>
    </Button>
  </PaginationPrev>
</template>
