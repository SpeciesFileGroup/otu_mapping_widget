<template>
  <div>
    <mapping-option
      v-for="(mappingOption, index) in mappingList"
      :key="index"
      @remove="removeOption(index)"/>
    <button type="button">
      Add another substitution
    </button>
  </div>
</template>

<script>

import MappingOption from './MappingOptions'

export default {
  components: {
    MappingOption
  },
  data () {
    return {
      mappingList: []
    }
  },
  methods: {
    removeOption (index) {
      this.mappingList.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
