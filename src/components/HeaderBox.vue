<template>
    
    <header class="container-fluid header d-flex">
        
        <div class="title-box">
            <h4 class="text-uppercase pt-4">boolflix</h4> 
        </div>
        
       
        <div class="input-group pt-3">

        <!-- 1. aggiungo v-model ad input con valore 'keywordSearch' -> sarà il titolo (o parte di esso) dei films filtrati e cercati tramite input -->
        <!-- 1.1 con @searching passo al padre (HeaderBox) in App.vue l'evento da scatenare -->
        <!-- 1.2 il $emit passa dal figlio (HeaderBox) al padre (App.vue) il dato e aggancia due parametri:
        il nome dell'avento (searching) che passa al padre e il valore passato dall'input tramite v-model 'keywordSearch'-->

        <input v-model="keywordSearch" type="text" class="form-control me-3" placeholder="Search your film" aria-label="Search">
        <button @click="$emit('searching', keywordSearch)" type="button" class="btn btn-light">Search</button>

    </div>
    </header>


    
</template>

<script>

export default {
    data() {
        return{
            keywordSearch: '',      // 2. salvo il valore dell'input in una variabile vuota -> sarà dinamica in base al testo digitato nell'input
                                    //  e conseguente alla ricerca effettuata dall'utente
        }
    }
}
</script>


<style lang="scss" scoped>
.header{
    height: 80px;
    background: black;

    .title-box{
        width: 80%;

        h4{
        color: red;
        }

    }

    .input-group{
    width: 400px;
    height: 50px;
}

    
}
</style>