<template>
    <main>
       <MovieList v-for="movie in movieCatalog" :key="movie.id" :info="movie"/>
    </main>
</template>

<script>
import MovieList from './MovieList.vue'
import axios from "axios"

export default {
      name: 'MainComponent',
      components: {
                MovieList,
                   },

                data() {
                        return{
                            MovieUrl: 'https://api.themoviedb.org/3/movie/550?api_key=ed5659a4d373a5fd2789a5e8e6b64fda',
                            movieCatalog: [],
                        }
                },
         created(){
             this.getMovies();
              },
        methods:{
        getMovies(){
            axios.get(this.MovieUrl).then((result) => {
                this.movieCatalog = result.data;
            })
            .catch((err) => {
                console.log("Error", err);
            });
        } }     
  
      } 
</script>

<style lang="scss" scope>
    main{
        margin-top: 200px;
    }
</style>