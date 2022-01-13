<template>

    <section class="d-flex flex-row">

        <div class="logo">
            <img src="../assets/logo.png" alt="logo">     
        </div>

      <div class="search-bar container d-flex">
        <input 
            v-model="searchText" 
            type="text" 
            class="form-control"  
            placeholder="Scegli un Film..."
        >
        
        <button @click="userSearch" class="btn">Ricerca</button>
        <!-- <button @click="$emit('searchDone', searchText)" class="btn">Ricerca</button> -->
        
    </div>

    </section>

</template>



<script>
export default {
    name: 'Header',
    data: function (){
        return {
            searchText: ''
        }
    },
    methods: {
        userSearch:function() {
            this.$emit('searchDone', this.searchText);
        }
    },
}
</script>

<style lang="scss" scoped>
template{
    
}
section{
    padding-top: 15px;
    padding-bottom: 15px;
    background-color: black;
    display: flex;
    justify-content: space-between;
    
    img{
        max-width: 175px;
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