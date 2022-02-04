<template>
    

    <!-- 6. con il v-for stampo tutti i film filtrati selezionandoli con :key=id 
    (l'id identificativo è nell'array che axios rimanda in risposta dopo la chiamata api) -->
    <!-- 6.1 MainContent (padre) dichiara il dato 'movie' che rimanderà sotto forma di props a FilmBox (figlio) -->

    
    <div class="main-content d-flex justify-content-center flex-wrap">
        <cards-box v-for="movie in movies" :key="movie.id" :movie="info"  />
        <cards-box v-for="serie in series" :key="serie.id" :serie="info"  />
    </div>

    
    

</template>

<script>
import CardsBox from "./CardsBox.vue"

export default{
    components: {
        CardsBox,
    },
    props: {
        movies: Array,    // importiamo i dati dal padre (App.vue) - riga 9 :movies="movies"
                         // -> nel mainContent, 'movies' rimanda un array di oggetti (ossia la lista dei film filtrati tramite input ricerca)
        series: Array,
    }
}
 
</script>


<style lang="scss" scoped>
.main-content{
    background-color: gray;
}


</style>