<script setup lang="ts">
import ElInput from './ElInput'

const emit = defineEmits(['add'])
const onAddItemClicked = () => {
  emit('add', {})
}
</script>
<template>
  <div>
    <button>뒤로</button>

    <h1>입력할 항목은?</h1>

    <div>
      <label>날짜</label>
      <ElInput />
    </div>
    <div>
      <label>용도</label>
      <ElInput />
    </div>
    <div>
      <label>금액</label>
      <ElInput />
    </div>
    <div>
      <label>지불(방법)</label>
      <ElInput />
    </div>
    <div>
      <label>내용</label>
      <ElInput />
    </div>
    <div>
      <label>비고</label>
      <ElInput />
    </div>
    <button @click="onAddItemClicked">add</button>
  </div>
</template>
