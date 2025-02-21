<script>
import listTable from './components/compList.vue'
import compControl from './components/compControl.vue'
import compAdd from './components/compAdd.vue'

import listTask from './data/task.js'

export default {
  name: 'app',
  data() {
    return {
      listTask: listTask,
    }
  },

  components: {
    listTable,
    compControl,
    compAdd,
  },
}
</script>

<template>
  <main>
    <div id="app">
      <div class="wrapper">
        <h1 class="text-6xl text-red-600 mt-40 mb-20 site-title">Todo List test</h1>

        <div class="block-control flex justify-between mb-20">
          <compControl />

          <div class="flex-1 pl-5">
            <compAdd />
          </div>
        </div>

        <listTable v-bind:listTask="listTask" />
      </div>
    </div>
  </main>
</template>

<style scoped>
.wrapper {
  max-width: 1240px;
  margin: auto;
  padding: 0 20px;
}
</style>
