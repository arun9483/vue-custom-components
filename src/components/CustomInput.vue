<template>
  <div class="custom-input">
    <div class="label-field" :class="{ focused: isFocused }">
      <label for="cinput">{{label}}</label>
    </div>
    <div class="text-field">
      <input 
        type="text"
        id="cinput"
        :placeholder="placeholder" 
        :value="rawValue"
        :pattern="pattern" 
        @input="inputHandler($event)" 
        @focus="focusHandler($event)"
        @blur="blurHandler($event)"/>
    </div>
    <div class="hint-field" :class="{ focused: isFocused }" v-if="isValid">
      <span>{{hint}}</span>
    </div>
    <div class="error-field" :class="{ focused: isFocused }" v-else>
      <span>{{errorMessage}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CustomInput',
  props: ['value', 'label', 'hint', 'placeholder', 'pattern'],
  data() {
    return {
      rawValue: this.value,
      isFocused: false,
      isValid: true,
      errorMessage: 'enter a valid email address',
    };
  },
  methods: {
    inputHandler($event) {
      this.rawValue = $event.target.value;
      this.isValid = $event.target.validity.valid;
      this.$emit('input', this.rawValue);
    },
    focusHandler() {
      this.isFocused = true;
    },
    blurHandler() {
      this.isFocused = false;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.custom-input {
  display: inline-block;
  text-align: left;
  .label-field {
    padding: 0.3rem 0.3rem;
    color: rgba(0, 0, 0, 0.5);
  }
  .label-field.focused {
    color: rgba(0, 0, 255, 1);
  }
  .text-field {
    input {
      padding: 0.2rem;
      min-height: 1.6rem;
      font-size: 1.1rem;
      color: rgba(0, 0, 0, 1);             
      outline-style: none;
      border-width: 0rem 0rem 0.05rem 0rem;
      border-style: solid;
      border-color: rgba(0, 0, 0, 0.9);
    }

    input:focus {
      border-width: 0rem 0rem 0.1rem 0rem;
      border-color: rgb(51, 36, 189);
    }
  }

  .error-field, .hint-field {
    padding: 0.3rem 0.3rem;
    color: rgba(0, 0, 0, 0.5);
  }
  .error-field.focused {
    color: rgba(255, 0, 0, 1);
  }
}
</style>
