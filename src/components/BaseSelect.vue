<template>
  <div>
    <label v-if="label">{{ label }}</label>
    <select type="text" :value="value" @input="updateValue" v-bind="$attrs" v-on="listeners">
      <option v-for="option in options" :key="option" :selected="option === value">{{
        option
      }}</option>
    </select>
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
    options: {
      type: Array,
      required: true
    },
    value: [String, Number]
  },
  computed: {
    listeners() {
      return {
        ...this.$listeners,
        input: this.updateValue
      };
    }
  },
  methods: {
    updateValue(event) {
      this.$emit('input', event.target.value);
    }
  }
};
</script>

<style scoped></style>
