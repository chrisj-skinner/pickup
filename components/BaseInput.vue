<template>
  <div class="field">
    <label v-if="label" class="label">{{ label }}</label>
    <div class="control">
      <input class="input" :type="type" v-bind="$attrs" @input="updateValue" />
    </div>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  props: {
    label: {
      type: String,
      default: ''
    },
    // eslint-disable-next-line
    type: [String, Number]
  },
  methods: {
    updateValue(item) {
      this.$emit('input', item.target.value)
    }
  }
}
</script>

<style scoped></style>
