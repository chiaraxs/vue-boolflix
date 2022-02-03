<template>
    

    <!-- 6. con il v-for stampo tutti i film con key obbligatoria index -->
    <div>
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

</style>