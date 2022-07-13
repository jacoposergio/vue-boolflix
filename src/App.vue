<template>
  <div id="app">
    <HeaderComponent @performSearch="search"/>
    <MainComponent
         :movieCards="movies"
         :searching="searchStarted"
    />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderComponent from './components/HeaderComponent.vue'
import MainComponent from './components/MainComponent.vue'


export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return{
        apiUrl: 'https://api.themoviedb.org/3/search/',
        apiKey: 'e99307154c6dfb0b4750f6603256716d',
        movies: [],
        series:[],
        AllResults:[],
        searchStarted: false
      }
   },
   methods: {
    getMovies(apiParams){
        axios.get(this.apiUrl + 'movie', apiParams)
        .then((response) => {
            this.movies = response.data.results;
        })
        .catch((err) => {
            console.log("Error", err);
        });
     },

    search: function (searchText) {
      const paramsObj = {
        params: {
          api_key: this.apiKey,
          query: searchText,
          languages: 'it-IT'
        }
      };
      this.getMovies(paramsObj);
    } 
  }    
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
