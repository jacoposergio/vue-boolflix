<template>
  <header>
     <div class="logo">logo</div>
     <SearchBarComponent/>
  </header>
</template>

<script>
import SearchBarComponent from './SearchBarComponent.vue'

export default {
       name: 'HeaderComponent',
       components: {
                SearchBarComponent
                   }
}
</script>

<style lang="scss" scoped> 

header{
    background-color: lightcyan;
    display: flex;
    justify-content: space-around;
}

</style>