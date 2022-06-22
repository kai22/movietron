<template>
  <AppHeader v-bind:title="title" v-bind:subtitle="subtitle"/>
  <!-- Search by title with optional year-->
  <SearchForm v-bind:inputs="inputs"  @submit.prevent="handleSubmit" />
  
  <FilmStrip /> <!-- just a visual element --> 
  
  <div class="contentWrapper">
    <!-- Loading div  --> 
    <div v-if="loading" class="loading"> &circlearrowright; </div>
    <!-- Error div  --> 
    <div v-if="errorMessage" class="error">
      <div class="error-message">
        <strong>Error!</strong><br />
        {{errorMessage}}
      </div>
    </div>
    <!-- Search Results -->
    <SearchResults v-if="searchResult" v-bind:results="searchResult"/>
  </div>

  <FilmStrip /> <!-- just a visual element --> 

  <AppFooter v-bind:footerText="footerText"/>
</template>

<script>

import FilmStrip from './components/FilmStrip.vue'
import AppHeader from './components/Header.vue'
import AppFooter from './components/Footer.vue'
import SearchForm from './components/SearchForm.vue'
import SearchResults from './components/SearchResults.vue'

export default {
  name: 'App',
  data() {
    return {
      title: 'MovieTron:5000',
      subtitle: 'Your movie search automaton',
      footerText: '&copy; 2022 Movietron LTD.  &nbsp;&nbsp;&nbsp;All rights Reserved.',
      searchResult:'',
      loading: false,
      errorMessage: '',
      inputs: [
        {
          label: 'Search by Title',
          type: 'text',
          placeholder: 'Enter Title',
          value:''
        },
        {
          label: 'Year (Optional)',
          type: 'text',
          placeholder: 'Enter Year',
          value:''
        }
      ],
    }
  },
  computed:{
    titleSearch:{
      get(){
        return this.inputs[0].value
      }
    },
    yearSearch:{
      get(){
        return this.inputs[1].value
      }
   }
  },
  components:{
    FilmStrip,
    AppHeader,
    SearchForm,
    SearchResults,
    AppFooter
  },
  methods:{
    fetchData(url){
      return fetch(url, {
        method: 'get',
      })
      .then(res => {
        // if it's a non-200 response code
        if (!res.ok) {
          // create error instance with HTTP status text
          const error = new Error(res.statusText);
          error.json = res.json();
          throw error;
        }

        return res.json();
      })

      .then(json => {
        // set the response data
        console.log(json);
        
        if (json.Response == 'False'){
          this.errorMessage = json.Error;
        } else {
          this.searchResult = json;
        }


      })
      .catch(err => {
        
        // In case a custom JSON error response was provided
        if (err.json) {
          return err.json.then(json => {
            // set the JSON response message
            this.errorMessage = json.message;
          });
        }
      })
      .then(() => {
        this.loading = false;
      });
    },
    reset() {
      this.errorMessage = '';
      this.searchResult = '';
    },
    handleSubmit() {
      this.reset();
      this.omdbSearch(this.titleSearch, this.yearSearch);
    },

    omdbSearch(t,y) {
      this.loading = true;

      let key = process.env.VUE_APP_OMDB_SEARCH_KEY;
      let title = t;
      let year = y;
      let url = `http://www.omdbapi.com/?apikey=${key}&t=${title}&y=${year}`;

      this.fetchData(url);
    }
  }
}
</script>

<style>

html {
  height: 100%
}

body {
  width: 80%;
  margin: 0px auto;
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100%;
  display: flex;
  flex-direction: column;
}

.error {
  display: flex;
  justify-content: center;
  width: 50%;
  height: 100px;
  font-size: 14px;
  background-color: rosybrown;
  margin: 15px auto;
}

.error-message {
  align-self: center;
}

.loading {
  display: block;
  width: 100px;
  height: 100px;
  font-size: 80px;
  margin: 0px auto;
  animation: spin 1s infinite linear;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

#app {
  display: flex;
  flex-direction: column;
  flex: 1;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}

.contentWrapper {
  flex: 1;
}

.double-line-horiz {
  height: 5px;
  border-top: 2px solid #666666;
  border-bottom: 2px solid #666666;
}

</style>
