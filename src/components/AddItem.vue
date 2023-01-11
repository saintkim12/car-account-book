<script setup lang="ts">

const emit = defineEmits(['add'])
const onAddItemClicked = () => {
  emit('add', {})
}
</script>
<template>
  <div>
    <button>뒤로</button>

    <h1>입력할 항목은?</h1>

    날짜

    용도

    금액

    지불(방법)

    내용

    비고

    <button @click="onAddItemClicked">add</button>
  </div>
</template>
