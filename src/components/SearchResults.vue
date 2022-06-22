<template>
  <section class="app-result">
    <img alt="Poster image" v-bind:src="results.Poster" class="result-image">

    <div class="result-data">
      <ul>
        <li><strong>Movie Title:</strong> {{results.Title}}</li>
        <li><strong>Director(s):</strong> {{results.Director}}</li>
        <li><strong>Genre:</strong> {{results.Genre}}</li>
        <li><strong>Release Date:</strong> {{results.Released}}</li>
      </ul>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'SearchResults',
    props: ['results']
  }
</script>

<style>
  .app-result {
    display: flex;
    flex-direction: row;
    justify-content: center;
    width: 75%;
    margin: 20px auto;
  }

  .result-image {
    width: 30%;
    height: auto;
    align-self: start;
    border: 1px solid #2c3e50;
  }

  .result-data {
    display: block;
    align-self: start;
    width: 50%;
    min-height: 100%;
  }

  .result-data > ul {
    list-style: none;
    margin: 0px;
    margin-left: 10px;
    padding: 0px;
    text-align: left;
  }

  .result-data > ul > li {
    background-color: #eeeeee;
    padding: 10px;
    margin-top: 3px;
    margin-bottom: 3px;
  }
</style>