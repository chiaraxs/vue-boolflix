<template>
    
    <header class="container-fluid d-flex header">
        
        <div class="container d-flex">

            <div class="logo-box d-flex">
                <img src="../assets/logo.jpg" alt="">
            </div>

            <div class="navbar d-flex ms-5 mt-2">
                <ul class="d-flex list-unstyled">
                    <li class="px-3">
                        <a href="#">Home</a>
                    </li>
                    <li class="px-3">
                        <a href="#">Film</a>
                    </li>
                    <li class="px-3">
                        <a href="#">Serie Tv</a>
                    </li>
                    <li class="px-3">
                        <a href="#">Nuovi e popolari</a>
                    </li>
                    <li class="px-3">
                        <a href="#">La mia lista</a>
                    </li>
                </ul>
            
            </div>
        
        
       
        </div>
        
        <div class="input-group pt-3 d-flex justify-content-end">

            <!-- 1. aggiungo v-model ad input con valore 'keywordSearch' -> sarà il titolo (o parte di esso) dei films filtrati e cercati tramite input -->
            <!-- 1.1 con @searching passo al padre (HeaderBox) in App.vue l'evento da scatenare -->
            <!-- 1.2 il $emit passa dal figlio (HeaderBox) al padre (App.vue) il dato e aggancia due parametri:
            il nome dell'avento (searching) che passa al padre e il valore passato dall'input tramite v-model 'keywordSearch'-->

            <input v-model="keywordSearch" @keyup.enter="$emit('searching', keywordSearch)" type="text" class="form-control me-3 border border-danger rounded" placeholder="Cerca il tuo film" aria-label="Search">
            <button @click="$emit('searching', keywordSearch)" type="button" class="btn text-light rounded">Cerca</button>
    
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
@import '@/style/variables.scss';

.header{
    height: 80px;
    background: $bg-color-header;

    .logo-box{
        width: 200px;
        margin-left: -150px;

        img{
            padding: 20px;
        }

    }
    
    li{
        &:hover{
            font-weight: bold;
            font-size: 18px;
        }            
        
        
        a{
            text-decoration: none;
            color: $secondary-color;
        }           
    }
    .input-group{
        width: 400px;
        height: 50px;

    button{
        background-color: $primary-color;
    }
}

    
}
</style>