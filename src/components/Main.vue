
<template>
  <div class="block" style="position:relative;top:50%;">
    <div class="columns is-multiline">
      <div class="column is-full"><button class="button is-fullwidth" @click="$emit('update-page', 'addItem')">항목 등록</button></div>
      <div class="column is-full"><button class="button is-fullwidth" @click="$emit('update-page', 'displayItem')">항목 조회</button></div>
      <div class="column is-full"><button class="button is-fullwidth" @click="$emit('update-page', 'appConfig')">설정</button></div>
    </div>
  </div>
</template>
