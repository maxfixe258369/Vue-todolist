<script>
import controlSort from './controlSort.vue'
import controlSearch from './controlSearch.vue'

export default {
  name: 'compControl',
  data() {
    return {}
  },

  components: {
    controlSort,
    controlSearch,
  },
}
</script>
<template>
  <div class="flex-1 pr-5">
    <controlSort />

    <controlSearch />
  </div>
</template>
