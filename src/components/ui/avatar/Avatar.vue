<script setup lang="ts">
import type { HTMLAttributes } from 'vue'
import { AvatarRoot } from 'radix-vue'
import { type AvatarVariants, avatarVariants } from '.'
import { cn } from '@/lib/utils'

interface Props {
  class?: HTMLAttributes['class']
  size?: AvatarVariants['size']
}

const props = withDefaults(defineProps<Props>(), {
  size: 'base',
})
</script>

<template>
  <AvatarRoot :class="cn(avatarVariants({ size }), props.class)">
    <slot />
  </AvatarRoot>
</template>
