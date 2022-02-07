<template>
  <div id="app">
    
    <!-- 5. passo ad Header-box (il genitore in ascolto dell'evento lanciato dal figlio HeaderBox) il dato/parametro 'searching' del $emit in HeaderBox. --> 
    <!-- 5.1 nel catturare l'avento, il padre richiama la funzione 'doSearch' che scatena l'evento e al click sul button fa la chiamata api  -->
    <!-- 5.2 App.vue (padre) dichiara i dati 'movies' e 'series' che rimanderà sotto forma di props a MainContent (figlio) -->

    <header-box @searching="doSearch" />       
    <main-content :movies="movies" :series="series" />    

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
      movies: [],    // 3. creo array vuoto che verrà popolato con i dati ricevuti dalla chiamata api x movies
      series: [],    // 3.1 creo anche array vuoto x series
      api_key: '9e033ce0eba533dff44afb04aca4ab7b',     // 3.2 dichiaro/conservo la mia api_key in una variabile
    }

  },
  mounted(){
    this.homeTrendingMovie();     // richiamo la funzione per popolare la home con nuova chiamata api per trending movies 
    this.homeTrendingSerie();     // stessa cosa, ma per series
  },
  methods: {
    // 4. creo 5 funzioni:
    // 'searchMovies' e 'searchSeries' ritornano la chiamata api in base ai parametri dichiarati ->
    // i 2 parametri sono: i valori (query & api_key) e le chiavi (query ossia richiesta lanciata ad axios & mia personale api key dichiarata nei data)
    // 'doSearch', invece, filtra tra series e movies nelle rispettive funzioni
    // 'homeTrendingMovie' e 'homeTrendingSerie' ritornano chiamata api in home con trending movie e serie
    searchMovies(query){
      const params = {
        query: query,      
        api_key: this.api_key,
      }

      return axios.get(`https://api.themoviedb.org/3/search/movie`, { params }).then((response) => {
        this.movies = response.data.results;    // api call -> salva nell'array vuoto 'movies' i dati ricevuti in risposta da axios
      });
    },
    searchSeries(query){
      const params = {
        query: query,      
        api_key: this.api_key,
      }

      return axios.get(`https://api.themoviedb.org/3/search/tv`, { params }).then((response) => {
        this.series = response.data.results;    // api call -> salva nell'array vuoto 'series' i dati ricevuti in risposta da axios
      });
    },
    doSearch(query){
      this.searchSeries(query);
      this.searchMovies(query);
    },
    homeTrendingMovie(query){
      const params = {
        query: query,
        api_key: this.api_key,
      }
      
      return axios.get(`https://api.themoviedb.org/3/trending/movie/day`, { params }).then((response) => {
        this.movies = response.data.results;       
      });
    },
    homeTrendingSerie(query){
      const params = {
        query: query,
        api_key: this.api_key,
      }
      
      return axios.get(`https://api.themoviedb.org/3/trending/tv/day`, { params }).then((response) => {
        this.series = response.data.results;       
      });
    },
  }  
}
</script>

<style lang="scss">
@import './style/common.scss';
@import url('https://fonts.googleapis.com/css2?family=The+Nautigal&display=swap');

</style>
