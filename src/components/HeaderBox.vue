<template>
    
    <header class="container-fluid header d-flex">
        
        <div class="title-box">
            <h4 class="text-uppercase pt-4">boolflix</h4> 
        </div>
        
       
       <search-bar />
    </header>


    
</template>

<script>
import SearchBar from './SearchBar.vue'

export default {
  components: { 
        SearchBar
    },
    data(){

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
    
}
</style>