<template>
    <li>
      <div class="card">
            <div class="movie-poster">
            <img 
            v-if="item.poster_path !== null"
              :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" 
              alt="movie poster"
            >
            <div v-else>
              <img src="../assets/img/notaviable.jpg" alt="image nto aviable">
            </div>
           </div> 
       
          <div>Titolo: {{item.title? item.title : item.name}}</div>
          <div>Titolo originale: {{item.original_title? item.original_title : item.original_name}}</div>
          <div class="language">
            <span>Lingua:  </span>
            <img
              v-if="langArray.includes(item.original_language)"
              :src="require(`../assets/flags/${item.original_language}.png`)" 
              :alt="item.original_language"
            >
            <div class="not-found" v-else>
              <img 
                  src="../assets/flags/notfound.png"
                  alt="language"
                >
                <div class="lang-notfound">{{item.original_language}}</div>
            </div>
          </div>
          <div class="rating">
              <div v-for="n in getStars(item.vote_average)" :key="n" class="full-star">&starf;</div>
              <div v-for="n in 5 - getStars(item.vote_average)" :key="n" class="blank-star">&star;</div>
          </div>  
      <div class="black-bg"></div>
      </div>    
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
         getStars(original_vote){
          return Math.round( original_vote / 2);
         }
         
     },
}

</script>

<style lang="scss" scoped>

li{
  margin-bottom: 1rem;
  color: white;
  display: flex;
  padding: 15px;


  .card{
    height: 513px;
    width: 342px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;

        .movie-poster{
          position: absolute;
          right: 0;
          top: 0;
          z-index: 0;
          cursor: pointer;
        }

        .movie-poster:hover{
          z-index: -1;
          opacity: 0.3;
          
        }
          .black-bg{
            height: 513px;
            width: 342px;
            position: absolute;
            right: 0;
            top: 0;
            z-index: -1;
            background-color: black;
            opacity: 40%;
        }

        .language{
          display: flex;
          align-items: center;

          span{
            margin-right: 10px;
          }

          img{
            width: 30px;
          }

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
        .rating{
          display: flex;
          justify-content: center;
          align-items: center;
          font-size: 25px;
        }



  }


}
  

</style>