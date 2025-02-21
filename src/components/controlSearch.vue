<script>
export default {
  name: 'controlSearch',
  data() {
    return {}
  },
}
</script>

<template>
  <div class="control-search flex">
    <input
      type="text"
      placeholder="Search for ..."
      class="flex-1 border border-black border-r-0 p-1 pl-4"
    />
    <button class="bg-blue-500 text-white w-50 p-2">Clear</button>
  </div>
</template>
