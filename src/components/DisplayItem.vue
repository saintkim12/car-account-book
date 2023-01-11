<script setup lang="ts">
import type { PropType } from 'vue';
import type { CarAccountItem } from '../App.vue';

const { items } = defineProps({ items: Object as PropType<CarAccountItem[]> })
</script>
<template>
  # | 날짜 | 용도 | 금액 | 지불(방법) | 내용 | 비고
  <br>
  ---------------------------------------------
  <br>
  item.count: {{ items!.length }}
</template>
