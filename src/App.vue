<template>
  <div id="app">
    <HeaderComponent @performSearch="search"/>
    <MainComponent
         :movieCards="AllResults"
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
            this.AllResults = [...this.series, ...this.movies]
        })
        .catch((err) => {
            console.log("Error", err);
        });
     },

     getSeries(apiParams){
        axios.get(this.apiUrl + 'tv', apiParams)
        .then((response) => {
            this.series = response.data.results;
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
      this.getSeries(paramsObj);
    } 
  }    
}
</script>

<style lang="scss">
@import'@/assets/scss/Common.scss';
 

</style>
