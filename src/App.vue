<template>
  <div id="app">
    
    <!-- 5. passo ad Header-box (il genitore in ascolto dell'evento lanciato dal figlio HeaderBox) il dato/parametro 'search' del $emit in HeaderBox. --> 
    <!-- 5.1 nel catturare l'avento, il padre richiama la funzione 'searchMovies' che scatena l'evento e al click sul button fa la chiamata api  -->
    <!-- 5.2 App.vue (padre) dichiara i dati 'movies' che rimanderà sotto forma di props a MainContent (figlio) -->

    <header-box @search="searchMovies" />       
    <main-content :movies="movies" />    

  </div>
</template>

<script>
import HeaderBox from './components/HeaderBox.vue';
import MainContent from './components/MainContent.vue';
import axios from 'axios';



export default {
  name: 'App',
  components: {
    HeaderBox,
    MainContent,
  },
  data(){
    return {
      movies: [],    // 3. creo array vuoto che verrà popolato con i dati ricevuti dalla chiamata api
      api_key: '9e033ce0eba533dff44afb04aca4ab7b',     // 3.1 dichiaro/conservo la mia api_key in una variabile
    }

  },
  methods: {
    // 4. creo la funzione che verrà chiamata da Header-Box
    // fisso 2 parametri: i valori (query & api_key) e le chiavi (query ossia richiesta lanciata ad axios & mia personale api key dichiarata nei data)
    // la funzione ritorna la chiamata api in base ai parametri dichiarati
    searchMovies(query){
      const params = {
        query: query,      
        api_key: this.api_key,
      }

      return axios.get(`https://api.themoviedb.org/3/search/movie`, { params }).then((response) => {
        this.movies = response.data.results;    // api call -> salva nell'array vuoto 'movies' i dati ricevuti in risposta da axios
      });
    },
  }  
}
</script>

<style lang="scss">
@import './style/common.scss';

</style>
