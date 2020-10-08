<template>
  <div id="app">
    <OtuWidget
      :name-list="otuList"
      column-name="Otu"
      column-match="Taxon name"
      :possible-matches-list="taxonList"
      @matched="setMatches"/>
  </div>
</template>

<script>

import OtuWidget from './components/OtuWidget'
import OtuList from '../resources/otus.json'
import taxonNames from '../resources/taxon_names.json'

export default {
  name: 'App',
  components: {
    OtuWidget
  },
  data () {
    return {
      otuList: OtuList,
      taxonList: taxonNames,
      matchedList: []
    }
  },
  methods: {
    setMatches (list) {
      this.matchedList = list
    }
  }
}
</script>

<style lang="scss">
</style>
