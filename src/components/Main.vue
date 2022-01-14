<template>

    <main>

        <h2 v-show='movies.length > 0'>Film: </h2>

        <div class="container d-flex"> 

            <div class="row row-cols-2 row-cols-lg-5 justify-content-center">            
                <Card
                    v-for = "movie in movies" 
                    :key="movie.id" 
                    :infoObj="movie"
                />                
            </div>

        </div>

        <h2 v-show='series.length > 0'>Serie Tv: </h2>

        <div class="container d-flex"> 

            <div class="row row-cols-2 row-cols-lg-5 justify-content-center">            
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
    
}
</style>