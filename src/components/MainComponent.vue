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

<style lang="scss" scoped>
@import'@/assets/scss/Common.scss';

    main{
         height: 100%;
         padding-top: 100px;

        ul {
         list-style-type: none;
         display: flex;
           }
    }

</style>