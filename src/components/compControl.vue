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

  props: {
    textSearch: {
      type: String,
    },

    orderBy: {
      type: String,
    },
  },

  methods: {
    handleGetText(data) {
      this.$emit('handleGetText', data)
    },

    handleSort(data) {
      this.$emit('handleSort', data)
    },
  },
}
</script>
<template>
  <div class="flex-1 pr-5">
    <controlSort v-bind:orderBy="orderBy" v-on:handleSort="handleSort" />

    <controlSearch v-bind:textSearch="textSearch" v-on:handleGetText="handleGetText" />
  </div>
</template>
