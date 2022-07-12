<template>
    <main>
       <MovieList/>
    </main>
</template>

<script>
import MovieList from './MovieList.vue'
import axios from "axios"

export default {
      name: 'MainComponent',
      components: {
                MovieList
                   },

                data() {
                        return{
                            MovieUrl: 'https://api.themoviedb.org/3/movie/433?api_key=ed5659a4d373a5fd2789a5e8e6b64fda',
                            movieCatalog: [],
                        }
                },
        methods:{
        getMovies(){
            axios.get(this.MovieUrl).then((result) => {
                this.movieCatalog = result.data.belongs_to_collection;
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