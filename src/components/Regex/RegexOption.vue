<template>
  <div>
    <div>
      <input
        v-model="mappingOption.enable"
        type="checkbox">
    </div>
    <div>
      <label>Replace this</label>
      <input
        type="text"
        v-model="mappingOption.found">
    </div>
    <div>
      <label>With this</label>
      <input
        type="text"
        v-model="mappingOption.replace">
    </div>
    <div>
      <button
        @click="removeOption"
        type="button">
        Remove
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Object
    },
    default: () => {
      return {
        enable: true,
        found: '',
        replace: ''
      }
    }
  },
  computed: {
    mappingOption: {
      get () {
        return this.value
      },
      set (value) {
        this.$emit('input', value)
      }
    }
  },
  methods: {
    removeOption () {
      this.$emit('remove')
    }
  }
}
</script>
