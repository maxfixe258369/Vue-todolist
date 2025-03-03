<script>
import listTable from './components/compList.vue'
import compControl from './components/compControl.vue'
import compAdd from './components/compAdd.vue'

import listTask from './data/task.js'

export default {
  name: 'app',

  components: {
    listTable,
    compControl,
    compAdd,
  },

  data() {
    return {
      listTask: listTask,
      isShowForm: false,
      textSearch: '',
      orderBy: 'Name Ascending',
      taskSelected: null,
    }
  },

  watch: {
    listTask: {
      handler(newTask) {
        var taskString = JSON.stringify(newTask)
        localStorage.setItem('database', taskString)
      },
      deep: true,
    },
  },

  created() {
    var data = localStorage.getItem('database')

    if (data !== null) {
      this.listTask = JSON.parse(data)
    } else {
      this.listTask = []
    }
  },

  methods: {
    handleGetText(data) {
      this.textSearch = data
    },

    handleSort(data) {
      this.orderBy = data
    },

    showForm() {
      if (this.isShowForm) this.taskEdit = null
      this.isShowForm = !this.isShowForm
    },

    compareName(a, b) {
      var numberName = this.orderBy === 'Name Ascending' ? -1 : 1
      if (a.name < b.name) return numberName
      else if (a.name > b.name) return numberName * -1
      else return 0
    },

    compareLevel(a, b) {
      var numberLevel = this.orderBy === 'Level Ascending' ? 1 : -1
      if (a.level < b.level) return numberLevel
      else if (a.level > b.level) return numberLevel * -1
      else return 0
    },

    handleDelete(data) {
      this.listTask = this.listTask.filter((item) => item.id !== data.id)
    },

    handleEdit(taskEdit) {
      this.isShowForm = true
      this.taskSelected = taskEdit
    },

    handleEditTask(taskEditObj) {
      this.listTask.forEach((item, index) => {
        if (item.id === taskEditObj.id) {
          this.listTask.splice(index, 1, taskEditObj)
        }
      })

      this.showForm()
    },

    handleAddTask(data) {
      this.listTask.push(data)
    },
  },

  computed: {
    getListSearch() {
      var newItems = []
      this.listTask.forEach((item) => {
        if (item.name.toLowerCase().includes(this.textSearch.toLowerCase())) {
          newItems.push(item)
        }
      })
      return newItems
    },

    listTaskSort() {
      var listTask = [...this.getListSearch]

      if (this.orderBy === 'Level Ascending' || this.orderBy === 'Level Descending') {
        listTask.sort(this.compareLevel)
      } else {
        listTask.sort(this.compareName)
      }

      return listTask
    },
  },
}
</script>

<template>
  <main>
    <div id="app">
      <div class="thumbnail">
        <img src="./assets/img/keyvisual_img.jpg" alt="thumbnail" />
      </div>
      <div class="section-main">
        <div class="wrapper">
          <h1 class="text-5xl mb-10 site-title">Todo List</h1>

          <div class="block-control flex justify-between mb-10">
            <compControl
              v-bind:textSearch="textSearch"
              v-bind:orderBy="orderBy"
              v-on:handleGetText="handleGetText"
              v-on:handleSort="handleSort"
            />

            <div class="flex-1 pl-5">
              <compAdd
                v-bind:taskSelected="taskSelected"
                v-bind:isShowForm="isShowForm"
                v-on:handleAddTask="handleAddTask"
                v-on:handleEditTask="handleEditTask"
                v-on:showForm="showForm"
              />
            </div>
          </div>

          <listTable
            v-bind:listTask="listTaskSort"
            v-on:handleDelete="handleDelete"
            v-on:handleEdit="handleEdit"
          />
        </div>
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
