<template>
  <div class="custom-components-container">
    <h3>{{msg}}</h3>
    <custom-input 
      v-model="value" 
      :label="label" 
      :hint="hint"
      :placeholder="placeholder"
      pattern="^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$"></custom-input>
    <br>
    {{value}}
  </div>
</template>

<script>
export default {
  name: 'custom-components-container',
  data() {
    return {
      msg: 'Custom Components Container',
      value: '',
      label: 'Enter your email',
      hint: 'email id',
      placeholder: 'Enter your email id',
    };
  },
  components: {
    CustomInput: () => import('@/components/CustomInput'),
  },
};
</script>

<style scoped>
.custom-components-container {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
