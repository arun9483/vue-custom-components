<template>
  <div class="custom-input">
    <input type="text" :value="rawValue" @input="inputHandler($event)" />
  </div>
</template>

<script>
export default {
  name: 'CustomInput',
  props: ['value'],
  data() {
    return {
      rawValue: this.value,
    };
  },
  methods: {
    inputHandler($event) {
      this.rawValue = $event.target.value;
      this.$emit('input', this.rawValue);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
