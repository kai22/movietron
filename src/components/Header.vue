<template>
  <header>
    <div class="double-line-horiz"></div>
    <div class="app-title">{{ title }}</div>
    <div class="app-subtitle">{{ subtitle }}</div>
    <div class="double-line-horiz"></div>
  </header>
</template>

<script>
  export default {
    name: 'AppHeader',
    props: ['title','subtitle']
  }
</script>

<style>
  .app-title {
    display: block;
    font-size: 60px;
    font-weight: bold;
    -webkit-transform:scale(1,.75); /* Safari and Chrome */
    -moz-transform:scale(1,.75); /* Firefox */
    -ms-transform:scale(1,.75); /* IE 9 */
    -o-transform:scale(1,7.5); /* Opera */
    transform:scale(1,.75); /* W3C */
  }
  .app-subtitle {
    display: block;
    font-size: 20px;
    font-style: italic;
  }
</style>