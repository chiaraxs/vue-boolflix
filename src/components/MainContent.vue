<template>
    

    <!-- 6. con il v-for stampo tutti i movies e series filtrati selezionandoli con :key=id 
    (l'id identificativo è nell'array che axios rimanda in risposta dopo la chiamata api) -->
    <!-- 6.1 MainContent (padre) dichiara i dati 'movie' e 'serie' che rimanderà sotto forma di props a CardsBox (figlio) -->
    <!-- 6.2 assegno anche un type (a cui dò valore 'string' in cardsBox), 
    per gestire la differenza di sintassi dell'array tra movies e series per title/name e originaltile/originalname -->
    <!-- 6.3 rimando props a figlio (CardsBox) :info -->

    <div class="main-box">
        <div class="main-content ">

            <!-- FILM -->
            <div>
                <h4 class="text-light text-center pt-5"> Film:</h4>
            </div>
            
            <div class="d-flex justify-content-center flex-wrap">
                <cards-box  v-for="movie in movies" :key="movie.id" :info="movie" :type="'movie'" :languages="languages" />
            </div>
            <!-- / FILM -->

            <!-- SERIE TV -->
            <div>
                <h4 class="text-light text-center pt-5">Serie Tv:</h4>
            </div>
            
            <div class="d-flex justify-content-center flex-wrap">
                <cards-box v-for="serie in series" :key="serie.id" :info="serie" :type="'serie'" :languages="languages"  />
            </div>
            <!-- / SERIE TV -->
            
            

            
        </div>
    </div>
    
    

    
    

</template>

<script>
import CardsBox from "./CardsBox.vue"

export default{
    components: {
        CardsBox,
    },
    props: {
        movies: Array,    // importiamo i dati dal padre (App.vue) - riga 9 :movies="movies" e :series="series" 
                         // -> nel mainContent, 'movies' e 'series' rimandano un array di oggetti (ossia la lista dei film/serie filtrati/e tramite input ricerca)
        series: Array,
        languages: Array,
    }
}
 
</script>


<style lang="scss" scoped>
@import '@/style/variables.scss';

.main-box{
    height: 100vh;
    background-color: $bg-color-main;

    .main-content{
        background-color: $bg-color-main;
        height: auto;
    }   
}



</style>