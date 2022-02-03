<template>
  <div id="app">
    
    <header-box />
    <main-content />

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
      movies: [],    // creo array vuoto che verrà popolato con i dati ricevuti dalla chiamata api
    }

  },
  mounted(){
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro').then((response) => {
    this.movies = response.data.results;    // chiamata api 
    console.log (response.data.results);     // console debug
    });
  } 
}
</script>

<style lang="scss">
@import './style/common.scss';

</style>
