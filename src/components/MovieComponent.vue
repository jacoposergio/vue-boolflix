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