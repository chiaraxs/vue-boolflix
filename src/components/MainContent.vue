<template>
    

    <!-- 6. con il v-for stampo tutti i film con key obbligatoria 'index' -->
    <div class="main-content d-flex justify-content-center flex-wrap">
        <films-box v-for="(movie, index) in movies" :key="index" :movie="movie"  />
    </div>
    

</template>

<script>
import FilmsBox from "./FilmsBox.vue"

export default{
    components: {
        FilmsBox,
    },
    props: {
        movies: Array,    // qui il movies rimanda un array
    }
}
 
</script>


<style lang="scss" scoped>
.main-content{
    background-color: gray;
}


</style>