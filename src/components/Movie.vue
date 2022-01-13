<template v-if="movieVisible">
        
    <div class="movie d-flex justify-content-center">
        <img :src="'https://image.tmdb.org/t/p/w342'+ movieObj.poster_path" alt="">

        <div class="detail">Titolo: <span class="obj">{{ movieObj.title}}</span> </div>
        
        <div class="detail">Titolo originale: <span class="obj"> {{ movieObj.original_title}} </span></div>
        
        <div class="detail">Lingua:  
            <span v-if="flags.includes(movieObj.original_language)" class="obj"> 
                <img 
                    class="flag" 
                    :src="require(`../assets/flags/${movieObj.original_language}.png`)" 
                    :alt="movieObj.original_language"
                > 
            </span>
            <span class="flag" v-else>
                {{movieObj.original_language}}
            </span>
        </div>

        <div class="detail">Voto: 
            <span class="star" v-for="n in 5" :key="n">
                <span class="star" v-if="n <= Vote()">
                    <i class="fas fa-star"></i>
                </span>
                <span class="star" v-else>
                    <i class="far fa-star"></i>
                </span>
            </span>  
        </div> 

    </div>

</template>


<script>

    export default {                          
        name: 'Movie',
        data: function() {
            return{
               flags: ['it', 'en', 'fr', 'es', 'de', 'ja'] 
            };
        },
        props: {
            movieObj: Object, 
            movieVisible: Boolean,
        },
        methods: {
            Vote: function(){
            let star = Math.ceil(this.movieObj.vote_average / 2)
            return star  
            },
        }
    
    };
    
</script>

<style scoped lang="scss" >
@import '../style/variables.scss';
@import '../style/general.scss';

.movie {
    flex-direction: column;
    align-items: center; 
    margin: 5px;      
    width: 350px;
    text-align: center;
    border: 3px solid black;
}   

</style>