<script>
export default {
  name: 'listItem',
  data() {
    return {}
  },

  props: {
    task: {
      type: Object,
    },

    index: {
      type: Number,
    },
  },

  computed: {
    getLevelName() {
      switch (this.task.level) {
        case 0:
          return 'High'
        case 1:
          return 'Medium'
        case 2:
          return 'Low'
        default:
          return ''
      }
    },

    getClassLevel() {
      switch (this.task.level) {
        case 0:
          return 'level-high'
        case 1:
          return 'level-medium'
        case 2:
          return 'level-low'
        default:
          return ''
      }
    },
  },

  methods: {
    handleDelete() {
      if (confirm('Do you want delete this task ?')) {
        this.$emit('handleDelete', this.task)
      }
    },

    handleEdit() {
      this.$emit('handleEdit', this.task)
    },
  },
}
</script>
<template>
  <tr>
    <td>{{ index }}</td>
    <td>{{ task.name }}</td>
    <td>
      <div class="level" v-bind:class="getClassLevel">{{ getLevelName }}</div>
    </td>
    <td>
      <button class="bg-yellow-500 text-white p-2" v-on:click="handleEdit">Edit</button>
      <button class="bg-red-500 text-white p-2 ml-2" v-on:click="handleDelete">Delete</button>
    </td>
  </tr>
</template>
