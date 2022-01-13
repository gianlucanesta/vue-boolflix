<template>
  <div id="app">
    <Header @searchDone='startSearch'/>
    <Main :movies='movieSearch' :series='serieSearch' />
    
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
import axios from 'axios';

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data: function() {
    return {
      queryValue:"",
      apiKey:'c2b6787a5025ee12b816659fac55db15',
      movieSearch:[],
      serieSearch: []
    }
  },
  methods: {
    startSearch: function(userString){
      // console.log('test')
      this.queryValue = userString;

      this.getContents();
      this.getSerie();
    },
    // Chiamata Api movies
    getContents: function() {
      axios.get(
        'https://api.themoviedb.org/3/search/movie', 
        {
          params: {
            api_key: this.apiKey,
            // api_key: 'c2b6787a5025ee12b816659fac55db15',
            query: this.queryValue,
          }
        }
      ).then ((response) => {
        // console.log(response);
        this.movieSearch = response.data.results;
      }); 
    },  
    // Chiamata Api series
    getSerie: function(){
      axios.get(
        'https://api.themoviedb.org/3/search/tv', 
        {
          params: {
            api_key: this.apiKey,
            // api_key: 'c2b6787a5025ee12b816659fac55db15',
            query: this.queryValue,
          }
        }
      ).then ((response) => {
        this.serieSearch = response.data.results;
      });
      
    },

  }
};
</script>

<style lang="scss">
  @import './style/general';

</style>