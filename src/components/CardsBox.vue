<template>
  
  <!-- 7. qui stampo i dati dei film  -->
    <div class="film-box  border border-dark my-3 mx-4"> 
      
        <div class="film-details">
            
            <!-- se il link dell'img ha valore === null -> stampa questa img -->
            <img class="not-found" id="show" v-if="info.poster_path === null " src="https://via.placeholder.com/1700/000000/FF0000/?text=Poster+not+available" alt="poster Not Avaible">
                
            <!-- altrimenti, se l'immagine è inclusa nel movie.poster_path -> stampala -->
            <img id="show" v-else :src="'https://image.tmdb.org/t/p/original/' + info.poster_path">  
        
        
        
            <div class="text-light py-4 px-3" id="hidden">

                <div class="movies" v-if="type === 'title'">
                    Titolo: {{info.title}}
                <br>
                <span class="fw-bold">Titolo originale:</span> {{info.original_title}}
                <br>
                <span class="fw-bold">Overview:</span> {{info.overview}}
                </div>


                <div class="series" v-else>
                    Titolo:{{info.name}}
                    Titolo Originale: {{info.original_name}}
                    Overview: {{info.overview}}
                </div>

    

                
            


            </div>
        </div>
        
        
    </div>
    
</template>

<script>


export default {
    props: {
        info: Object,   // importiamo i dati dal padre (Maincontent - riga 8 :movie="movie) 
                        // -> 'movie' in film.box rimanda un object ( ossia i singoli films compresi nell'array di oggetti filtrati, 
                        // inclusi title, original_title, overview e altri dettagli )
    type: String
    
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