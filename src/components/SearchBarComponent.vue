<template>
  <div class="search-bar">
        <input
                class="form-control"
                type="text"
                placeholder="Search a movie"
                v-model="text"
          />
         <div>
            <button 
                type="submit"
                class="btn btn-success"
                >
                Search
            </button>
         </div>          
  </div>
</template>

<script>

export default {
      name: 'SearchBarComponent',
       data(){
        return{
            text: ''
        }
    },
    }

</script>

<style lang="scss" >

   .search-bar{
     display: flex;

     button{
    margin-left: 1rem;
     }
   }
</style>