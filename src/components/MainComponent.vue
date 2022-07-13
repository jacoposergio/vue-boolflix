<template>
    <main>
        <ul class="cards">
           <MovieComponent 
             v-for="card in movieCards"
             :key="card.id"
             :item="card"
            />
       </ul>
    </main>
</template>

<script>
import MovieComponent from './MovieComponent.vue'

export default {
      name: "MainComponent",
      props: {
        "movieCards": Array,
        "searching" : Boolean
      },
      components: {
          MovieComponent,
       }
   } 
</script>

<style lang="scss" scope>
    main{
        margin-top: 200px;

        ul {
         list-style-type: none;
         margin-bottom: 1rem;
           }
    }
</style>