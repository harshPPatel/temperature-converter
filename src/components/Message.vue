<template>
  <div class="message" :class="{ 'is-cold': isCold }">
    <p>{{ getMessage() }}</p>
  </div>
</template>

<script>
export default {
  props: {
    isCold: {
      type: Boolean,
      required: true
    }
  },
  methods: {
    getMessage: function() {
      return this.isCold ? "It's too Cold!" : "It's too Hot!";
    }
  }
};
</script>

<style lang="scss" scoped>
// Colors
$primary-color: #f6554d;
$secondary-color: #132f63;

.message {
  display: inline-block;
  position: fixed;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  border: 5px solid $primary-color;
  background-color: white;
  padding: 20px 30px;
  p {
    font-size: 28px;
    font-weight: 800;
    display: inline-block;
    color: $primary-color;
    margin: 0;
  }

  &.is-cold {
    border-color: $secondary-color;
    p {
      color: $secondary-color;
    }
  }
}
</style>
