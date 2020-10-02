<template>
  <table>
    <thead>
      <tr>
        <th>Select</th>
        <th>OTU name</th>
        <th>Modifier for mapping</th>
        <th>Taxon name</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="(otu, index) in otuList"
        :key="index.id">
        <td>
          <input
            :value="index"
            v-model="selected"
            type="checkbox">
        </td>
        <td>{{ otu.name }}</td>
        <td>
          <input
            type="text"
            v-model="temporaryNameList[index]">
        </td>
        <td>{{ mappedTaxon[index] }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>

export default {
  props: {
    otuList: {
      type: Array
    },
    taxonList: {
      type: Array
    },
    mappedTaxon: {
      type: Array
    },
    temporaryNameList: {
      type: Array,
      default: () => []
    },
    mappingOptions: {
      type: Array,
      default: () => []
    },
    value: {
      type: Array,
      default: () => []
    }
  },
  computed: {
    selected: {
      get () {
        return this.value
      },
      set (value) {
        this.$emit('input', value)
      }
    }
  }
}
</script>
