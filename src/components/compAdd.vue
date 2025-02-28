<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  name: 'compAdd',
  data() {
    return {
      taskName: '',
      level: -1,
    }
  },

  props: {
    isShowForm: {
      type: Boolean,
    },
    taskSelected: {
      type: Object,
    },
  },

  watch: {
    taskSelected: function (newData) {
      this.taskName = newData.name
      this.level = newData.level
    },
  },

  methods: {
    showForm() {
      this.$emit('showForm')
    },

    closeForm() {
      this.$emit('showForm')
      this.resetData()
    },

    handleAddTask() {
      if (this.taskName == '' || this.level < 0) {
        alert('Please enter full information !!')
      } else {
        var newTask = {
          id: uuidv4(),
          name: this.taskName,
          level: parseInt(this.level),
        }
        this.$emit('handleAddTask', newTask)
        this.closeForm()
      }
    },

    handleEditTask() {
      var taskEdit = {
        id: this.taskSelected.id,
        name: this.taskName,
        level: parseInt(this.level),
      }
      this.$emit('handleEditTask', taskEdit)
      this.resetData()
    },

    resetData() {
      this.taskName = ''
      this.level = -1
    },
  },
}
</script>
<template>
  <div class="control-add">
    <button
      class="bg-blue-500 text-white text-center p-2 mb-5 w-full text-xl"
      v-on:click="showForm"
    >
      Add task
    </button>
    <div class="add-main flex" id="formAdd" v-if="isShowForm">
      <form action=""></form>
      <input
        v-model="taskName"
        type="text"
        class="add-name border border-black flex-1 p-1 pl-4"
        placeholder="name"
      />
      <select v-model="level" name="prior" class="w-30 border border-black p-2 ml-2">
        <option value="-1" hidden>Level</option>
        <option value="0">High</option>
        <option value="1">Medium</option>
        <option value="2">Low</option>
      </select>
      <button
        v-if="taskSelected === null"
        v-on:click="handleAddTask"
        class="w-20 bg-green-500 hover:bg-green-700 transition text-white mr-2 ml-2"
      >
        Submit
      </button>
      <button
        v-else
        v-on:click="handleEditTask"
        class="w-20 bg-green-500 hover:bg-green-700 transition text-white mr-2 ml-2"
      >
        Update
      </button>
      <button
        class="w-20 bg-gray-500 hover:bg-gray-700 transition text-white"
        v-on:click="closeForm"
      >
        Cancel
      </button>
    </div>
  </div>
</template>
