<template>
  
  <!-- 7. qui stampo i dati dei film  -->
    <div class="film-box  border border-dark my-3 mx-4"> 
      
        <div class="film-details">
            <!-- se il link dell'img ha valore === null -> stampa questa img -->
            <img class="not-found py-5" id="show" v-if="movie.poster_path === null" src="https://www.freeiconspng.com/thumbs/no-image-icon/no-image-icon-15.png" alt="">
                
            <!-- altrimenti, se l'immagine è inclusa nel movie.poster_path -> stampala -->
            <img id="show" v-else :src="'https://image.tmdb.org/t/p/original/' + movie.poster_path">  
        
        
        
            <div class="text-light py-4 px-3" id="hidden">
                <span class="fw-bold">Titolo:</span> {{movie.title}}
                <br>
                <span class="fw-bold">Titolo originale:</span> {{movie.original_title}}
                <br>
                <span class="fw-bold">Overview:</span> {{movie.overview}}
            </div>
        </div>
        
        
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
    width: (100% / 7);
    background-color: black;
    
        
        
    img{
        width: 100%;
        height: 100%;
    }

    #hidden{
        display: none;
       
    }

    .film-details{
        cursor: pointer;
        height: 500px;

        
    }

    &:hover .film-details{
        
        #show{
            display: none;
            
            
        }

        #hidden{
            display: block;
            line-height: 15px;
        }
        
    }
}


</style>