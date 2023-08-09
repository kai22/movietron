<template>
  <div class="box-separator">
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
  </div>
</template>

<script>
  export default {
    name: 'FilmStrip',
  }
</script>

<style>
  .box {
    width: 20px;
    height: 20px;
    background-color: #eeeeee;
    border: 1px solid #cccccc;
    margin:3px;
    align-self: center;
  }

  .box-separator {
    display: flex;
    flex-direction: row;
    justify-content: center;
    width: 80%;
    margin: 10px auto;
  }
</style>