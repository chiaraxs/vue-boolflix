<template>
  
  <!-- 7. qui stampo i dati dei film  -->
    <div class="film-box text-center"> 
        <img :src="'https://image.tmdb.org/t/p/original/' + movie.poster_path">  
        <h3>{{movie.title}}</h3>
        <h4>{{movie.original_title}}</h4>
        <div>{{movie.original_language}}</div>
        <div>{{movie.vote_avarage}}</div>
    </div>
    
</template>

<script>


export default {
    props: {
        movie: Object,   // qui movie rimanda un object
    }
    
}
</script>


<style lang="scss" scoped>
.film-box{
    height: 100vh;
    background-color: gray;
}


</style>