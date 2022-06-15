<template>
  <form class="app-search">
    
    <CustomInput 
      v-for="(input, i) in inputs"
      :key="i"
      :label="input.label"
      :type="input.type"
      v-model="input.value" />
   
    <button>Go!</button>
  </form>
</template>

<script>
  import CustomInput from '../components/CustomInput.vue'

  export default {
    name: 'SearchForm',
    props:['inputs'],
    components:{
      CustomInput
    }
  }
</script>

<style>
  .app-search {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin: 20px auto;
    width: 50%;
    
    /* border: 1px solid #2c3e50; */
  }

  button {
    width: 75px;
    height: 50px;
    font-size: 18px;
    margin: 0px;
    padding: 0px;
  }
</style>
