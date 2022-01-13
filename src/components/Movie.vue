<template v-if="movieVisible">
        
    <div class="movie d-flex justify-content-center">
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

        <div class="detail">Voto: <span class="obj"> {{ movieObj.vote_average}} </span></div> 
    </div>

</template>


<script>

    export default {                          
        name: 'Movie',
        data: function() {
            return{
               flags: ['it', 'en', 'fr', 'es', 'de', 'ja' ] 
            };
        },
        props: {
            movieObj: Object, 
            movieVisible: Boolean,
        },
    
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
    padding: 30px;
    border: 3px solid black;
}

.detail {
   font-weight: bold;
}

.obj {
    font-weight: lighter;
}


    

</style>