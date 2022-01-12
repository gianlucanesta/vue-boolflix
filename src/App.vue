<template>
  <div id="app">
    <Header @movies='startSearch'/>
    <Main :movies='resultSearch' />
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
      searchedValue:"",
      resultSearch:[],

    }
  },
  methods: {
    startSearch: function(searchCompleted){
      console.log('test')

      this.searchedValue = searchCompleted;
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'c2b6787a5025ee12b816659fac55db15',
          query: this.searchedValue,
        }
      }).then ((response) => {
        this.resultSearch = response.data.results;
      });
    }
  }
};
</script>

<style lang="scss">
  @import './style/general';

</style>