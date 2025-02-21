<script>
export default {
  name: 'compAdd',
  data() {
    return {}
  },

  methods: {
    addForm() {
      const form = document.getElementById('formAdd')
      form.style.display = 'block'
    },

    removeForm() {
      const form = document.getElementById('formAdd')
      form.style.display = 'none'
    },
  },
}
</script>
<template>
  <div class="control-add">
    <button class="bg-blue-500 text-white text-center p-2 mb-5 w-full text-xl" v-on:click="addForm">
      Add task
    </button>
    <div class="add-main flex hidden" id="formAdd">
      <input type="text" class="add-name border border-black flex-1 p-1 pl-4" placeholder="name" />
      <select name="prior" class="w-20 border border-black p-2 ml-2">
        <option value="level" disabled>level</option>
        <option value="High">High</option>
        <option value="Medium">Medium</option>
        <option value="Small">Small</option>
      </select>
      <button class="w-20 bg-green-500 hover:bg-green-700 transition text-white mr-2 ml-2">
        Submit
      </button>
      <button
        class="w-20 bg-gray-500 hover:bg-gray-700 transition text-white"
        v-on:click="removeForm"
      >
        Cancel
      </button>
    </div>
  </div>
</template>
