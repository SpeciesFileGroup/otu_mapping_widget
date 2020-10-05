<template>
  <div>
    <mapping-view
      v-model="mappingOptions"
      @mapping="mappingTaxon"/>
    <list-component
      v-model="selectedOtus"
      :otu-list="otuList"
      :taxon-list="taxonList"
      :temporary-name-list="temporaryNameList"
      :mapped-taxon="mappedTaxon"/>
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
      mappingOptions: [],
      temporaryNameList: [],
      mappedTaxon: [],
      selectedOtus: []
    }
  },
  watch: {
    mappingOptions: {
      handler (newVal) {
        this.temporaryNameList = this.otuList.map(otu => this.getTemporaryName(otu.name))
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
    mappingTaxon () {
      this.mappedTaxon = this.temporaryNameList.map(name => this.taxonList.filter(taxon => taxon.name === name))
    }
  }
}
</script>
