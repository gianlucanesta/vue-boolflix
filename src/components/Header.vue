<template>

    <section class="d-flex flex-row">

        <div class="logo">
            <img src="../assets/logo.png" alt="logo">     
        </div>

      <div class="search-bar container d-flex">
        <input 
            v-model="searchMovie" 
            type="text" 
            class="form-control"  
            placeholder="Scegli un Film..."
        >
        
        <button @click="searchCompleted" class="btn">Ricerca</button>
    </div>

    </section>

</template>



<script>
export default {
    name: 'Header',
    data: function (){
        return {
            searchMovie: '',
        }
    },
    methods: {
        searchCompleted:function() {
            this.$emit('movies', this.searchMovie);
        }
    },
}
</script>

<style lang="scss" scoped>
template{
    background-color: black;
}
section{
    padding-top: 15px;
    padding-bottom: 15px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    
    img{
        width: 175px;
        margin: 0 20px;
    }
    .search-bar {
        margin: auto 20px;
        button {
            margin-left: 20px;
            background-color: #e50914;
            color: white;
            
            cursor: pointer;
        }
    }
}
</style>