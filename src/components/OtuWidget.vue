<template>
  <div>
  </div>
</template>

<script>
export default {
  props: {
    otuList: {
      type: Array,
      default: () => []
    },
    taxonList: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      mappers: [],
      mappingOptions: []
    }
  }
}
</script>
