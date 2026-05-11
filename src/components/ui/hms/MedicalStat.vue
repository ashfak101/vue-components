<script setup lang="ts">
import { type HTMLAttributes } from 'vue'
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card'
import { cn } from '@/lib/utils'

interface Props {
  title: string
  value: string | number
  unit?: string
  description?: string
  trend?: {
    value: string
    type: 'up' | 'down' | 'neutral'
  }
  icon?: any
  class?: HTMLAttributes['class']
}

const props = defineProps<Props>()
</script>

<template>
  <Card :class="cn('overflow-hidden', props.class)">
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
      <CardTitle class="text-sm font-medium">
        {{ title }}
      </CardTitle>
      <component
        :is="icon"
        v-if="icon"
        class="h-4 w-4 text-muted-foreground"
      />
    </CardHeader>
    <CardContent>
      <div class="flex items-baseline space-x-1">
        <div class="text-2xl font-bold">{{ value }}</div>
        <div v-if="unit" class="text-xs font-medium text-muted-foreground">{{ unit }}</div>
      </div>
      <div v-if="description || trend" class="flex items-center mt-1">
        <span
          v-if="trend"
          :class="cn(
            'text-xs font-medium mr-1',
            trend.type === 'up' ? 'text-green-600' : trend.type === 'down' ? 'text-red-600' : 'text-muted-foreground'
          )"
        >
          {{ trend.value }}
        </span>
        <p v-if="description" class="text-xs text-muted-foreground">
          {{ description }}
        </p>
      </div>
    </CardContent>
  </Card>
</template>
