<template>

    <main>

        <h2 v-show='movies.length > 0'>Film: </h2>

        <div class="container"> 

            <div class="row-container d-flex">
                <Card
                    v-for = "movie in movies" 
                    :key="movie.id" 
                    :infoObj="movie"
                />
            </div>
            
        </div>

        <h2 class="mt-5" v-show='series.length > 0'>Serie Tv: </h2>

        <div class="container"> 

            <div class="row-container d-flex">            
                <Card
                    v-for = "serie in series" 
                    :key="serie.id" 
                    :infoObj="serie"
                />                
            </div>

        </div>

    </main>
    
</template>

<script>
import Card from "./Card.vue";
export default {
    name: 'Main',
    components: {
        Card
    },
    
    props: {
        movies: Array,
        series: Array,
    },
}
</script>

<style lang="scss" scoped>

main {
    margin-top: 30px;

    h2 {
        margin-left: 15%;
        margin-bottom: 20px;
    }
    
    // Scrollable only with keyboard arrow left and right
    .container {
        overflow-x: hidden;
        overflow-x: scroll;  
    }

    .row-container {
        width: 95%;
        margin: 45px;
    }

    .container::-webkit-scrollbar {
    display: none;
}


    
}
</style>