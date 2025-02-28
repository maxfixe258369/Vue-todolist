<script>
export default {
  name: 'controlSort',
  data() {
    return {}
  },

  methods: {
    handleSort(e) {
      this.$emit('handleSort', e.target.value)
    },
  },

  props: {
    orderBy: {
      type: String,
    },
  },
}
</script>

<template>
  <div class="control-sort mb-5 flex">
    <select
      name="sort"
      class="bg-gray-500 text-white p-2 mr-4 text-xl outline-none cursor-pointer"
      v-on:change="handleSort"
    >
      <option value="sortby" hidden>Sort by</option>
      <option value="Name Ascending">Name Ascending</option>
      <option value="Name Descending">Name Descending</option>
      <option disabled></option>
      <option value="Level Ascending">Level Ascending</option>
      <option value="Level Descending">Level Descending</option>
    </select>

    <div class="sort-text bg-green-400 text-white font-medium p-2 text-xl">{{ orderBy }}</div>
  </div>
</template>
