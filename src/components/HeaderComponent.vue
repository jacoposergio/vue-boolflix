<template>
  <header>
     <div class="logo">logo</div>
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

header{
    background-color: lightcyan;
    display: flex;
    justify-content: space-around;

    .search-bar{
     display: flex;

     button{
    margin-left: 1rem;
     }
   }
}

</style>