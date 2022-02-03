<template>
  
  <!-- 7. qui stampo i dati dei film  -->
    <div class="film-box text-center border border-dark my-2 mx-1"> 
      
        <!-- se il link dell'img ha valore === null -> stampa questa img -->
        <img class="not-found" v-if="movie.poster_path === null" src="https://bitsofco.de/content/images/2018/12/broken-1.png" alt="">
            
        <!-- se l'immagine è inclusa nel movie.poster_path -> stampala -->
        <img v-else :src="'https://image.tmdb.org/t/p/original/' + movie.poster_path">  
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

    .not-found{
       
        padding: 30px;
      
    }
}


</style>