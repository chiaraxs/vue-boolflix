<template>
    
    <div class="input-group pt-3">

        <!-- 1. aggiungo v-model ad input con valore 'keywordSearch' riferito al titolo del film cercato tramite input -->
        <!-- 1.1 con @search passo al padre (HeaderBox) in App.vue l'evento  -->
        <!-- 1.2 $emit aggancia due parametri: il nome dell'avento (search) che passa al padre e il valore passato dall'input tramite v-model -->
        <input v-model="keywordSearch" type="text" class="form-control me-3" placeholder="Search your film" aria-label="Search">
        <button @click="$emit('search', keywordSearch)" type="button" class="btn btn-light">Search</button>
    </div>

</template>


<script>
export default {
    data() {
        return{
            keywordSearch: '',      // 2. salvo il valore dell'input qui -> così sarà dinamico in base alla ricerca effettuata dall'utente
        }
    }
    
}
</script>


<style lang="scss" scoped>

.input-group{
    width: 400px;
    height: 50px;
}

</style>