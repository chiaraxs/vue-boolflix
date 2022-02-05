<template>
  
  <!-- 7. qui stampo i dati dei film  -->

    <div class="film-box border border-dark my-2 mx-2"> 
      
        <div class="film-details">
            
            <!-- se il link dell'img ha valore === null -> stampa questa img -->
            <img class="not-found" id="show" v-if="info.poster_path === null " src="https://unsplash.it/200/300?image=876" alt="posterNotAvaible">
                
            <!-- altrimenti, se l'immagine è inclusa nel movie.poster_path -> stampala -->
            <img id="show" v-else :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`">  
        
        
        
            <div class="text-light py-4 px-3" id="hidden">

                <div class="movies-series">
                    
                    <!--8. il ternario mi semplifica la sintassi per differenziare type 'movie' e 'serie'-> 
                    il type è === a 'movie'? allora lancia istruzione 1 (info.title) + istruzione 2 (info.name)  
                    il type è === a 'movie'? allora lancia istruzione 1 (info.original_title) + istruzione 2 (info.original_name)  --> 

                    <span class="fw-bold">Titolo:</span> {{type === 'movie' ? info.title : info.name}}
                    <br>
                    <span class="fw-bold">Titolo originale:</span> {{type === 'movie' ? info.original_title : info.original_name}}
                    <br>
                    <span class="fw-bold">Overview:</span> {{info.overview}}
                    <br>
                    <span class="fw-bold">Language: <img :src="`/flags/${info.original_language}.png`" alt="flags" class="ms-2"></span>                      
                    <br>
                    <span class="fw-bold">Vote:</span> {{info.vote_average}}

                </div>

            </div>
        </div>
        
        
    </div>
    
</template>

<script>


export default {
    props: {
        info: Object,   // importiamo i dati dal padre (Maincontent - riga 13/14) 
                        // -> 'info' rimanda un object ( ossia i singoli films compresi nell'array di oggetti filtrati, 
                        // inclusi title, original_title, overview e altri dettagli )
        
        type: String,       // importo type con valore String per differenziare movie/serie
    
    }
    
}
</script>


<style lang="scss" scoped>

.film-box{
    width: (100% / 6);

   .film-details{
        background-color: #d5001f;
   }
    
        
        
    img{
        object-fit: cover;
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
            line-height: 18px;
        }
        
    }

    .movies-series{
        img{
            width: 30px;
        }
    }
}


</style>