<script setup lang="ts">
import type { Show } from '@/types/show'

interface Props {
  showData: Show
}

defineProps<Props>()
</script>
<template>
  <div class="min-w-[270px]">
    <div class="flex text-burgundy items-center gap-2 px-2">
      <div class="text-5xl w-[85px]">{{ showData.date }}</div>
      <div class="flex flex-col gap-1">
        <span class="text-4xl">{{ showData.cityName }}, {{ showData.stateName }}</span>
        <span class="text-2xl">{{ showData.eventName }}</span>
        <router-link to="" class="text-gray-400">Saiba mais</router-link>
      </div>
    </div>
    <Button class="bg-burgundy py-3 px-4 rounded mt-5 w-full text-xl">Comprar ingressos</Button>
  </div>
</template>
