<template>
  <table border="1">
    <thead>
      <tr>
        <th>Select</th>
        <th>{{ columnName }}</th>
        <th>Modifier for mapping</th>
        <th>{{ columnMatch }}</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="(otu, index) in nameList"
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
          <button
            type="button"
            @click="removeTemporaryName(index)">
            Remove
          </button>
        </td>
        <td>
          <div v-if="mappedList[index]">
            <span v-if="mappedList[index].length > 1">Possible mappings</span>
            <button
              v-if="mappedList[index].length"
              type="button">
              Remove
            </button>
            <ul>
              <li
                v-for="(item, mIindex) in mappedList[index]"
                :key="mIindex">
                <button
                  type="button"
                  @click="acceptMatch(otu, item, index)">
                  Accept
                </button>
                {{ item }}
              </li>
            </ul>
          </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>

export default {
  props: {
    nameList: {
      type: Array
    },
    taxonList: {
      type: Array
    },
    mappedList: {
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
    columnName: {
      type: String,
      required: true
    },
    columnMatch: {
      type: String,
      required: true
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
  },
  data () {
    return {
      matchesList: []
    }
  },
  methods: {
    acceptMatch (name, mappedName, nameIndex) {
      const matched = {
        name: name,
        matched: mappedName
      }
      this.matchesList.push(matched)
      this.$emit('matched', {
        mapped: matched,
        index: nameIndex
      })
    },
    removeTemporaryName (index) {
      this.$set(this.temporaryNameList, index, undefined)
    }
  }
}
</script>
