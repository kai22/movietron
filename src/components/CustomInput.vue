<template>
  <label>
    <strong>{{label}}</strong> <br />
    <input v-bind:placeholder="placeholder" v-bind:type="type" v-model="inputValue" />
  </label>
</template>

<script>
  export default {
    name: 'CustomInput',
    props: ['label','type','placeholder','modelValue'],
    computed: {
      inputValue: {
        get() {
            return this.modelValue
        },
        set(v) {
            this.$emit('update:modelValue', v)
        }
      }
    },
  }
</script>

<style>
  label {
    display: block;
    width: 40%;
    text-align: left;
    align-self: center;
  }

  input {
    font-size: 14px;
    width: 90%;
    height: 16px;
    margin-bottom: 10px;
    padding-top: 4px;
  }

  input::placeholder{
    font-size: 14px;
    font-style: italic;
    color: #cccccc;
  }
</style>