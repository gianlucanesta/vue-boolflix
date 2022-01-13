<template>
    <div class="container d-flex">
        <input 
            v-model="searchMovie" 
            type="text" 
            class="form-control"  
            placeholder="Scegli un Film..."
        >
        <!-- <button @click="$emit('searchQuery', searchMovie)" type="button" class="btn btn-danger">Search</button> -->
        <button @click="searchCompleted" class="btn">Ricerca</button>
    </div>
</template>


<script>
export default {
    name: "Search",
    data: function() {
        return {
            searchMovie: ''
        };

    },
    methods: {
        searchCompleted:function() {
            this.$emit('searchQuery', this.searchMovie);
        }
    },
}
</script>

<style scoped lang="scss">
@import '../style/variables.scss';

button {
    margin-left: 20px;
    background-color: #860000;
    color: white;
    
    cursor: pointer;
}

button:hover {
    background-color: #ed0000;
    color: white;
}

.form-control {
    border: 1px solid black;
}


</style>