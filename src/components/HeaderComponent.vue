<template>
  <header>
     <div class="logo">
      <img src="../assets/img/netflix.png" alt="">
     </div>
    <div class="search-bar">
        <input
                class="form-control"
                type="text"
                placeholder="Search a movie"
                v-model="inputText"
                @keyup.enter="$emit('performSearch',inputText)"
          >
         <div>
            <button 
                @click="$emit('performSearch',inputText)"
                type="submit"
                class="btn btn-success"
                >
                Search
            </button>
         </div>          
     </div>
  </header>
</template>

<script>
export default {
       name: "HeaderComponent",
       data: function () {
        return {
            inputText: ''
        }
    }
}
</script>

<style lang="scss" scoped> 
@import'@/assets/scss/Common.scss';


header{
    position: fixed;
    left: 0;
    background-color:#232627;
    display: flex;
    justify-content: space-between;
    padding: 10px 50px;
    align-items: center;
    z-index: 10;
    width: 100%;

    .logo{
     
     img{
      width: 120px;
     }
      
    }

    .search-bar{
     display: flex;
      align-items: center;


     input{
       border-radius: 4px;
       height: 25px;
     }

     button{
     margin-left: 1rem;
     padding:0 8px;
     }
   }
}

</style>