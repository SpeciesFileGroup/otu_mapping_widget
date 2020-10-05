<template>
  <div>
    <button
      type="button"
      @click="$emit('mapping')">Map otus</button>
    <template v-for="(mappingOption, index) in mappingList">
      <regex-option
        :key="index"
        v-model="mappingList[index]"
        @remove="removeOption(index)"/>
    </template>
    <select v-model="optionSelected">
      <option
        v-for="(option, index) in regexOptions"
        :key="index"
        :value="option.value">
        {{ option.label }}
      </option>
    </select>
    <button
      type="button"
      @click="addNew(optionSelected)">
      Add another substitution
    </button>
  </div>
</template>

<script>

import RegexOption from './RegexOption'

export default {
  components: {
    RegexOption
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
  data () {
    return {
      regexOptions: [
        {
          label: 'Add a common substitution...',
          value: {
            found: '',
            replace: ''
          }
        }
      ],
      optionSelected: {
        found: '',
        replace: ''
      }
    }
  },
  methods: {
    removeOption (index) {
      this.mappingList.splice(index, 1)
    },
    addNew (value) {
      this.mappingList.push(Object.assign({}, { enable: true }, value))
    }
  }
}
</script>
