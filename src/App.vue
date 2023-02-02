<script setup lang="ts">
import { onMounted, Ref, ref, unref, watch } from 'vue'
import localforage from 'localforage'
import AddItem from './components/AddItem.vue'
import DisplayItem from './components/DisplayItem.vue'
import AppConfig from './components/AppConfig.vue'
import Main from './components/Main.vue'

export type CarAccountItem = Record<string, any>

const page = ref('')
const items: Ref<CarAccountItem[]> = ref([])
const addItem = (newItem: CarAccountItem) => {
  items.value.push(newItem)
}
const clearItems = async () => {
  items.value = []
  await localforage.setItem('items', [])
}
onMounted(async () => {
  console.log('localforage', localforage)
  try {
    const storedItems = (await localforage.getItem<CarAccountItem[]>('items')) ?? []
    items.value = storedItems
  } catch (e) {
    console.error(e)
  }
  watch(
    items,
    (v) => {
      console.log('items', JSON.parse(JSON.stringify(v)))
      localforage.setItem('items', JSON.parse(JSON.stringify(v))).then(async () => {
        console.log('items', await localforage.getItem<CarAccountItem[]>('items'))
      })
    },
    { deep: true }
  )
})
</script>

<template>
  <template v-if="page === 'addItem'">
    <AddItem v-bind="{}" @add="addItem"></AddItem>
  </template>
  <template v-else-if="page === 'displayItem'">
    <DisplayItem v-bind="{ items }"></DisplayItem>
  </template>
  <template v-else-if="page === 'appConfig'">
    <AppConfig v-bind="{}"></AppConfig>
  </template>
  <template v-else>
    <Main @update-page="(p) => page = p" />
  </template>
  <!-- @NOTE: 감춤 -->
  <div v-if="false" class="block">
    <div class="columns">
      <div class="column is-2">
        <button class="button" @click="page = 'addItem'">AddItem</button>
        <button @click="page = 'displayItem'">DisplayItem</button>
        <button @click="page = 'appConfig'">AppConfig</button>
        <button @click="clearItems">clearItems</button>
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
<style>
html,
body,
#app {
  width: 100%;
  height: 100%;
}

html,
body,
#app {
  margin: 0;
  padding: 0;
}
</style>
