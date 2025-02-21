<script>
export default {
  name: 'controlSort',
  data() {
    return {}
  },
}
</script>

<template>
  <div class="control-sort mb-5 flex">
    <select name="sort" class="bg-gray-500 text-white p-2 mr-4 text-xl">
      <option value="sortby" disabled>Sort by</option>
      <option value="nameasc">Name Ascending</option>
      <option value="namedsc">Name Descending</option>
      <option value="levelasc">Level Ascending</option>
      <option value="leveldsc">Level Descending</option>
    </select>

    <div class="sort-text bg-green-400 text-white font-medium p-2 text-xl">Name Ascending</div>
  </div>
</template>
