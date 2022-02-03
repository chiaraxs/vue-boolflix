<template>
  
  <!-- 7. qui stampo i dati dei film  -->
    <div class="film-box text-center border border-dark px-3 py-3 my-2 mx-1"> 
      
        <img :src="'https://image.tmdb.org/t/p/original/' + movie.poster_path">  
        <h5 class="mt-1">{{movie.title}}</h5>
        <h6>Language: {{movie.original_language}}</h6>
        <h6>{{movie.vote_avarage}}</h6>
        
        
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
    width: (100% / 6);
    background-color: gray;
        
        
    img{
        width: 100%;
    }
}


</style>