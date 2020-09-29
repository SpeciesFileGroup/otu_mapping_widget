<template>
  <tr>
    <td>
      {{ otu.name }}
    </td>
    <td></td>
    <td></td>
  </tr>
</template>

<script>
export default {
  props: {
    otu: {
      type: Object,
      required: true
    },
    mappingOptions: {
      type: Array,
      default: () => []
    }
  },
  methods: {

  }
}
</script>
