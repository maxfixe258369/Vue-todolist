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
      <button>Edit</button>
      <button>Delete</button>
    </td>
  </tr>
</template>
