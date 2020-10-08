<template>
  <div>
    <mapping-view
      v-model="mappingOptions"
      @mapping="mappingList"/>
    <list-component
      v-model="selectedOtus"
      :name-list="nameList"
      :column-name="columnName"
      :column-match="columnMatch"
      :taxon-list="possibleMatchesList"
      :temporary-name-list="temporaryNameList"
      :mapped-list="mappedList"
      @matched="addMatched"/>
  </div>
</template>

<script>

import ListComponent from './List'
import MappingView from './Regex/Main'

export default {
  components: {
    ListComponent,
    MappingView
  },
  props: {
    nameList: {
      type: Array,
      default: () => []
    },
    possibleMatchesList: {
      type: Array,
      default: () => []
    },
    columnName: {
      type: String,
      required: true
    },
    columnMatch: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      mappers: [],
      mappingOptions: [],
      temporaryNameList: [],
      mappedList: [],
      selectedOtus: [],
      matchedNames: []
    }
  },
  watch: {
    mappingOptions: {
      handler (newVal) {
        this.temporaryNameList = this.nameList.map(otu => this.getTemporaryName(otu.name))
      },
      deep: true
    }
  },
  methods: {
    getTemporaryName (name) {
      this.mappingOptions.forEach(regx => {
        if (regx.enable) {
          try {
            const re = new RegExp(regx.found)
            name = name.replace(re, regx.replace)
          } catch (error) {}
        }
      })
      return name.trim()
    },
    mappingList () {
      this.mappedList = this.temporaryNameList.map(name => this.possibleMatchesList.filter(taxon => taxon.name === name))
    },
    addMatched (event) {
      this.matchedNames.push(event.mapped)
      this.nameList.splice(event.index, 1)
      this.mappedList.splice(event.index, 1)
    }
  }
}
</script>
