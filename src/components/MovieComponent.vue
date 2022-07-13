<template>
    <li>
        <div>Titolo:{{item.title}}</div>
        <div>Titolo originale: {{item.original_title}}</div>
        <div>Lingua: {{item.original_language}}</div>
        <div>Voto: {{item.vote_average}}</div>
    </li>
</template>

<script>
export default {
    name: 'MovieComponent',
    data: function () {
      return{

      };
    },
    props:{
       "item": Object
    } 
}

</script>

<style lang="scss" scoped>

li{
  margin-bottom: 1rem;
}

</style>