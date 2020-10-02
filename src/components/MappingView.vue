<template>
  <div>
    <button
      type="button"
      @click="$emit('mapping')">Map otus</button>
    <template v-for="(mappingOption, index) in mappingList">
      <mapping-option
        :key="index"
        v-model="mappingList[index]"
        @remove="removeOption(index)"/>
    </template>
    <button
      type="button"
      @click="addNew">
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
  props: {
    value: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    mappingList: {
      get () {
        return this.value
      },
      set (value) {
        this.$emit('input', value)
      }
    }
  },
  methods: {
    removeOption (index) {
      this.mappingList.splice(index, 1)
    },
    addNew () {
      this.mappingList.push({
        enable: true,
        found: '',
        replace: ''
      })
    }
  }
}
</script>
