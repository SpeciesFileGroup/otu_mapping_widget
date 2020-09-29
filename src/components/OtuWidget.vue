<template>
  <div>
    <list-component
      :otu-list="otuList"
      :taxon-list="taxonList"/>
  </div>
</template>

<script>

import ListComponent from './List'

export default {
  components: {
    ListComponent
  },
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
