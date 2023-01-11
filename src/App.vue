<script setup lang="ts">
import { Ref, ref } from 'vue'
import AddItem from './components/AddItem.vue'
import DisplayItem from './components/DisplayItem.vue'
import AppConfig from './components/AppConfig.vue'

export type CarAccountItem = Record<string, any>

const page = ref('')
const items: Ref<CarAccountItem[]> = ref([])
const addItem = (newItem: CarAccountItem) => {
  items.value.push(newItem)
}
</script>

<template>
  <div class="block">
    <div class="columns">
      <div class="column is-2">
        <button class="button" @click="page = 'addItem'">AddItem</button>
        <button @click="page = 'displayItem'">DisplayItem</button>
        <button @click="page = 'appConfig'">AppConfig</button>
      </div>
      <div class="column">
        <template v-if="page === 'addItem'">
          <AddItem v-bind="{}" @add="addItem"></AddItem>
        </template>
        <template v-else-if="page === 'displayItem'">
          <DisplayItem v-bind="{ items }"></DisplayItem>
        </template>
        <template v-else-if="page === 'appConfig'">
          <AppConfig v-bind="{}"></AppConfig>
        </template>
        <template v-else>기본페이지</template>
      </div>
    </div>
  </div>
  <!-- <div> -->
  <!-- <a href="https://vitejs.dev" target="_blank"> -->
  <!-- <img src="/vite.svg" class="logo" alt="Vite logo" /> -->
  <!-- </a> -->
  <!-- <a href="https://vuejs.org/" target="_blank"> -->
  <!-- <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" /> -->
  <!-- </a> -->
  <!-- </div> -->
  <!-- <HelloWorld msg="Vite + Vue" /> -->
</template>

<style lang="scss">
@import 'bulma/bulma.sass';
</style>
<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
