<template>
  <table>
    <thead>
      <tr>
        <th>OTU name</th>
        <th>Modifier for mapping</th>
        <th>Taxon name</th>
      </tr>
    </thead>
    <tbody>
      <row-component
        v-for="otu in otuList"
        :key="otu.id"
        :otu="otu"/>
    </tbody>
  </table>
</template>

<script>

import RowComponent from './Row'

export default {
  components: {
    RowComponent
  },
  props: {
    otuList: {
      type: Array
    },
    taxonList: {
      type: Array
    }
  }
}
</script>
