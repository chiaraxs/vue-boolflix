<template>
  
  <!-- 7. qui stampo i dati dei film  -->

    <div class="film-box border border-dark mt-5 mx-1"> 
      
        <div class="film-details">
            
            <!-- se il link dell'img ha valore === null -> stampa questa img -->
            <img class="not-found" id="show" v-if="info.poster_path === null " src="https://unsplash.it/200/300?image=876" alt="posterNotAvaible">
                
            <!-- altrimenti, se l'immagine è inclusa nel movie.poster_path -> stampala -->
            <img id="show" v-else :src="`http://image.tmdb.org/t/p/w342/${info.poster_path}`">  
        
        
        
            <div class="text-light py-4 px-3" id="hidden">

                <!-- DETTAGLI MOVIES-SERIES -->
                <div class="movies-series">
                    
                    <!--8. il ternario mi semplifica la sintassi per differenziare type 'movie' e 'serie'-> 
                    il type è === a 'movie'? allora lancia istruzione 1 (info.title) + istruzione 2 (info.name)  
                    il type è === a 'movie'? allora lancia istruzione 1 (info.original_title) + istruzione 2 (info.original_name)  --> 

                    <div><strong>Titolo:</strong> {{type === 'movie' ? info.title : info.name}} </div>
                    <div><strong>Titolo originale:</strong> {{type === 'movie' ? info.original_title : info.original_name}}:</div>
                    <div><strong>Overview:</strong> {{info.overview}}</div>
                    
                    <!-- LANGUAGES -->
                    <div><strong>Lingue:</strong>
                        

                        <!-- se la lingua è compresa tra quelle indicata nei data, nell'array 'languages', rimanda la bandierina corrispondente -->
                        <!-- altrimenti, rimanda il nome della lingua senza bandiera -->

                        <!-- FLAGS -->
                       <img 
                        v-if="languages.includes(info.original_language)" :src="`/flags/${info.original_language}.png`" alt="flags" class="ms-2"/>
                        <span class="text-uppercase" v-else> {{ info.original_language }}</span>
                        <!-- /FLAGS -->

                    </div>
                    <!-- / LANGUAGES -->
                    
                    <!-- STARS - StarsAverage component -->
                    <stars-average :vote="info.vote_average" /> 
                    <!-- / STARS - StarsAverage component -->
                   
                </div>
                <!-- / DETTAGLI MOVIES-SERIES -->

            </div>
        </div>
        
        
    </div>
    
</template>

<script>
import StarsAverage from "./StarsAverage";


export default {
    components: {
       StarsAverage,
    },
    props: {
        info: Object,
          // importiamo i dati dal padre (Maincontent - riga 13/14) 
                        // -> 'info' rimanda un object ( ossia i singoli films compresi nell'array di oggetti filtrati, 
                        // inclusi title, original_title, overview e altri dettagli )
        
        type: String,       // importo type con valore String per differenziare movie/serie
        languages: Array,
    },
}
</script>


<style lang="scss" scoped>
@import '@/style/variables.scss';

.film-box{
    width: calc(100% / 6);

   .film-details{
        background-color: $primary-color;
        
        &:hover{
            filter: alpha(opacity=50);
            opacity: 0.9;
        }            
        
   }
    
        
        
    img{
        object-fit: fill;
        width: 100%;
        height: 100%;
    }

    #hidden{
        display: none;
    }

    .film-details{
        cursor: pointer;
        height: 500px;
        overflow-y: auto;
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