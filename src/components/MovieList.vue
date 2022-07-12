<template>
  <div class="movie-list">
    <ul>
        <li>{{info.title}}</li>
        <li>Titolo originale</li>
        <li>lingua</li>
        <li>voto</li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'MovieList',
    props: ['info']
}

</script>

<style lang="scss" scoped>

</style>