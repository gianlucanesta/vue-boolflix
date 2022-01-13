<template>

    <main>

        <h2 v-show='movies.length > 0'>Film: </h2>

        <div class="container d-flex"> 

            <div class="row row-cols-2 row-cols-lg-5 justify-content-center">            
                <Movie 
                    v-for = "movie in movies" 
                    :key="movie.id" 
                    :movieObj="movie"
                    :movieVisible="true"
                />                
            </div>

        </div>

        <h2 v-show='series.length > 0'>Serie Tv: </h2>

        <div class="container d-flex"> 

            <div class="row row-cols-2 row-cols-lg-5 justify-content-center">            
                <Serie 
                    v-for = "serie in series" 
                    :key="serie.id" 
                    :serieObj="serie"
                    :serieVisible="true"
                />                
            </div>

        </div>




    </main>
    
</template>

<script>
import Movie from "./Movie.vue";
import Serie from "./Serie.vue";

export default {
    name: 'Main',
    components: {
        Movie,
        Serie
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