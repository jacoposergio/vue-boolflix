<template>
    <li>
        <div>Titolo:{{item.title}}</div>
        <div>Titolo originale: {{item.original_title}}</div>
         <div >
          <img 
            v-if="`https://countryflagsapi.com/png/${item.original_language}`.loaded === false"
            :src="`https://countryflagsapi.com/png/${item.original_language}`" 
            alt="language"
            @load="`https://countryflagsapi.com/png/${item.original_language}`.loaded = true"
           >
            <img 
            v-else
            src="https://countryflagsapi.com/png/br" 
            alt="language"
           >
        </div>
        <!-- v-if="item.original_language === 'it'">Lingua: {{item.original_language}}</div> -->
        <div>Voto: {{item.vote_average}}</div>
    </li>
</template>

<script>

export default {
    name: 'MovieComponent',
    data: function () {
      return{
         isLoaded: false
      };
    },
    props:{
       "item": Object
    }, 
     methods: {
          onImgLoad () {
          this.isLoaded = true
        }
     },
}

</script>

<style lang="scss" scoped>

li{
  margin-bottom: 1rem;
}

</style>