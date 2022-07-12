<template>
  <div class="movie-list">
    <ul>
        <li>{{info.genres}}</li>
        <li>{{info.name}}</li>
        <li>lingua</li>
        <li>voto</li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'MovieList',
    props:{
        info: Object,
    }
}

</script>

<style lang="scss" scoped>

</style>