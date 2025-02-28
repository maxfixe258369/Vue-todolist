<script>
export default {
  name: 'controlSearch',
  data() {
    return {}
  },

  props: {
    textSearch: {
      type: String,
    },
  },

  methods: {
    handleGetText(e) {
      this.$emit('handleGetText', e.target.value)
    },

    clearSearch() {
      this.$emit('handleGetText', '')
    },
  },
}
</script>

<template>
  <div class="control-search flex">
    <input
      v-bind:value="textSearch"
      v-on:input="handleGetText"
      type="text"
      placeholder="Search for ..."
      class="flex-1 border border-black border-r-0 p-1 pl-4 outline-none"
    />
    <button class="bg-blue-500 text-white w-50 p-2" v-on:click="clearSearch">Clear</button>
  </div>
</template>
