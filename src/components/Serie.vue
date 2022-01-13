<template v-if="serieVisible">

    <div class="container serie d-flex justify-content-center">
        <img :src="'https://image.tmdb.org/t/p/w342'+ serieObj.poster_path" alt="">

        <div class="detail">Titolo: <span class="obj">{{ serieObj.name}}</span> </div>

        <div class="detail">Titolo originale: <span class="obj"> {{ serieObj.original_title}} </span></div>
    
        <div class="detail">Lingua:  
            <span v-if="flags.includes(serieObj.original_language)" class="obj"> 
                <img 
                    class="flag" 
                    :src="require(`../assets/flags/${serieObj.original_language}.png`)" 
                    :alt="serieObj.original_language"
                > 
            </span>
            <span class="flag" v-else>
                {{serieObj.original_language}}
            </span>
        </div>

        <!-- <div class="detail">Voto: <span class="obj"> {{ serieObj.vote_average}}</span>  </div>  -->
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
        name: 'Serie',
        data: function() {
            return{
               flags: ['it', 'en', 'fr', 'es', 'de', 'ja'] 
            };
        },
        props: { 
            serieObj: Object,
            serieVisible: Boolean,
        },
        methods: {
            Vote: function(){
            let star = Math.ceil(this.serieObj.vote_average / 2)
            return star  
            }
        }
    
    };
    
</script>

<style scoped lang="scss" >
@import '../style/variables.scss';
@import '../style/general.scss';

.serie{
    flex-direction: column;
    align-items: center; 
    margin: 5px;      
    width: 350px;
    text-align: center;
    border: 3px solid black;
}

 

</style>


