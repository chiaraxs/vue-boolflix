<template>
  <div id="app">
    
    <!-- 3. passo ad header-box la funzione 'searchMovie' che scatena l'evento e al click sul button fa la chiamata api -->
    <header-box @search="searchMovie"/>       
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
      movies: [],    // 4. creo array vuoto che verrà popolato con i dati ricevuti dalla chiamata api
    }

  },
  methods: {
    // 5. creo la funzione che verrà chiamata da Header-Box
    searchMovie(keyword){
      return axios.get(`https://api.themoviedb.org/3/search/movie/?api_key=9e033ce0eba533dff44afb04aca4ab7b&query=${keyword}`).then((response) => {
      this.movies = response.data.results;    // api call -> salva nell'array vuoto movies i dati ricevuti in risposta da axios
      });
    }
  }  
}
</script>

<style lang="scss">
@import './style/common.scss';

</style>
