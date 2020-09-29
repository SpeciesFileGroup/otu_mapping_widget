<template>
  <div id="app">
    <OtuWidget
      :otu-list="otuList"
      :taxon-list="taxonList"/>
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
      taxonList: taxonNames
    }
  }
}
</script>

<style lang="scss">
</style>
