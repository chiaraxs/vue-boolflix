<template>
    
    <div>
        <strong>Voto:</strong> 
        <i v-for="star in starsAverageCalc" :key="star" class="fas fa-star ms-1"></i>
    </div>

</template>


<script>
export default {
    props: {
        vote: Number,
    },
    computed: {
        starsAverageCalc (){
            return Math.round(this.vote / 2);     // funzione che divide il punteggio totale / 2 -> il punteggio così sarà sulla base di max 5 stelline 
        }
    }
    
}
</script>



<style lang="scss" scoped>
@import '@/style/variables.scss';

</style>