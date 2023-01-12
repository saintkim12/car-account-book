<script setup lang="ts">
import { ref } from 'vue';

const activated = ref(false)

</script>
<template>
  <div @click="activated = true">
    <input type="text" />
  </div>
  <Teleport v-if="activated" to="#app">
    <div class="input__mask" @click="activated = false">
    </div>
  </Teleport>
</template>
<style lang="scss" scoped>
// .input__mask--activated {
.input__mask {
  position: fixed;
  background-color: #888;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: .5;
}
</style>