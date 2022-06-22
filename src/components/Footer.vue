<template>
  <footer>
    <div class="double-line-horiz"></div>
    <div class="app-footer" v-html="footerText">
    </div>
    <div class="double-line-horiz"></div>
  </footer>
</template>

<script>
  export default {
    name: 'AppFooter',
    props: ['footerText']
  }
</script>

<style>
  .app-footer {
    margin-top:5px;
    margin-bottom:5px;
    padding: 5px;
    background-color: #666666;
    color: white;
    font-size: 10px;
    font-weight: bold;
  }


  footer {
    margin-bottom: 10px;
  }

</style>