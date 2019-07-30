<template>
  <input
    type="number"
    :name="name"
    :id="id"
    size="1"
    :value="value"
    @input="changeHandler"
    step="0.1"
    :autofocus="autofocus"
  />
</template>

<script>
export default {
  name: "Input",
  props: {
    value: {
      required: true
    },
    name: {
      type: String,
      required: true
    },
    id: {
      type: String,
      required: true
    },
    autofocus: {
      type: Boolean,
      required: false
    }
  },
  methods: {
    changeHandler(event) {
      this.$emit("convert-value", event.target.value);
    }
  }
};
</script>

<style lang="scss" scoped>
// Colors
$primary-color: #f6554d;
$secondary-color: #132f63;

input {
  height: auto;
  width: 100%;
  max-width: 450px;
  font-size: 150px;
  font-family: "Muli", Helvetica, Arial;
  font-weight: 300;
  text-align: center;
  border: none;
  outline: none;
  background: transparent;
  border-bottom: 4px solid rgba($primary-color, 0.5);

  &:focus {
    border-color: $primary-color;
  }
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}
</style>
