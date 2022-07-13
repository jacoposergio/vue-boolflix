<template>
    <li>
        <div>Titolo: {{item.title}}{{item.name}}</div>
        <div>Titolo originale: {{item.original_title}}{{item.original_name}}</div>
         <div>
          <img
            v-if="langArray.includes(item.original_language)"
            :src="require(`../assets/flags/${item.original_language}.png`)" 
            alt="language"
           >
           <div class="not-found" v-else>
             <img 
                src="../assets/flags/notfound.png"
                alt="language"
              >
              <div class="lang-notfound">{{item.original_language}}</div>
           </div>
        </div>
        <div class="movie-poster">
          <img 
          v-if="item.poster_path !== null"
            :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" 
            alt="movie poster"
          >
          <div v-else>
            <img src="../assets/img/notaviable.jpg" alt="">
          </div>
        </div>
        <div>Voto: {{item.vote_average}} </div>
    </li>
</template>

<script>

export default {
    name: 'MovieComponent',
    data: function () {
      return{
        langArray : ["it", "en", "ja", "es", "de", "pt"]
        
      };
    },
    props:{
       "item": Object
    }, 
     methods: {
      
         
     },
}

</script>

<style lang="scss" scoped>

li{
  margin-bottom: 1rem;
}

.not-found{
  position: relative;
    .lang-notfound{
         position: absolute;
         right: 0;
         left: 0;
         top: 25px;
}
}


</style>