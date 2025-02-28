<script>
import listItem from './compListItem.vue'

export default {
  name: 'listTable',
  data() {
    return {}
  },

  components: {
    listItem,
  },

  props: {
    listTask: {
      type: Array,
    },
  },

  methods: {
    handleDelete(data) {
      this.$emit('handleDelete', data)
    },
    handleEdit(taskEdit) {
      this.$emit('handleEdit', taskEdit)
    },
  },
}
</script>

<template>
  <div class="list-task">
    <h2 class="list-title text-2xl bg-gray-200 p-3 border-t border-b border-black mb-5">
      List task
    </h2>
    <table class="w-full">
      <thead>
        <tr>
          <th class="w-1/6">#No</th>
          <th class="w-3/6">Task name</th>
          <th class="w-1/6">Level</th>
          <th class="w-2/6">Action</th>
        </tr>
      </thead>

      <tbody>
        <listItem
          v-for="(task, index) in listTask"
          v-bind:key="task.id"
          v-bind:task="task"
          v-bind:index="index + 1"
          v-on:handleDelete="handleDelete"
          v-on:handleEdit="handleEdit"
        />
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
