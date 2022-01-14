<template>
        
    <div class=" d-flex justify-content-center">
        
        <a href='#' class="box">
        
            <div v-if="infoObj.poster_path != null">
                <img class="cover" :src="'https://image.tmdb.org/t/p/w342'+ infoObj.poster_path" alt="">
            </div>
            
            <div v-else>
                <img class="cover not-found" src="../assets/not-found.jpg" alt="">
            </div>

            <div class="overlay">

                <!-- Titolo -->
                <div class="detail title">Titolo: 
                    <span class="obj">
                        {{ infoObj.title ? infoObj.title : infoObj.name}}
                    </span> 
                </div>

                <!-- Titolo Originale -->
                <div class="detail title">Titolo originale: 
                    <span class="obj"> {{ infoObj.original_title ? infoObj.original_title : infoObj.name}} </span></div>
                
                <!-- Lingua -->
                <div class="detail">Lingua:  
                    <span v-if="flags.includes(infoObj.original_language)" class="obj"> 
                        <img 
                            class="flag" 
                            :src="require(`../assets/flags/${infoObj.original_language}.png`)" 
                            :alt="infoObj.original_language"
                        > 
                    </span>

                    <!-- Bandiera -->
                    <span class="flag" v-else>
                        {{infoObj.original_language}}
                    </span>
                </div>

                <!-- Voto -->
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

                <!-- Overview -->
                <div class="title detail">Overview:
                    <span class="obj detail">
                        {{infoObj.overview}}
                    </span>
                </div>
                
            </div>
        </a>
    </div>

</template>


<script>

    export default {                          
        name: 'Card',
        data: function() {
            return{
               flags: ['it', 'en', 'fr', 'es', 'de', 'ja'] 
            };
        },
        props: {
            infoObj: Object, 
            movieVisible: Boolean,
            serieVisible: Boolean,
        },
        methods: {
            Vote: function(){
            let star = Math.ceil(this.infoObj.vote_average / 2)
            return star  
            },
        }
    
    };
    
</script>

<style scoped lang="scss" >
@import '../style/variables.scss';
@import '../style/general.scss';

.flag {
    width: 25px;
}

.star {
    color: #ffbd00;
}

.detail {
    font-weight: bold;
}
 
.obj {
    font-weight: lighter;
}

.box {
    flex-direction: column;
    align-items: center; 
    margin: 10px;      
    width: 350px;
    text-align: center;
    border: 1px solid white;
    cursor: pointer;
    transition: transform .5s ease;
} 

.cover{
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.not-found {
    height: 325px;
}

.box:hover {
    transform: scale(1.2);
}
  
.overlay{
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0,0,0,.9);
    padding: 5px 10px;
    transition: all .5s ease;
    opacity: 0;
    pointer-events: none;
    overflow-y: scroll;
}

.overlay::-webkit-scrollbar {
    display: none;
}
  
.box:hover .overlay{
    opacity: 1;
    pointer-events: all;
}
  
.overlay .title{
    color: #e9e9e9;
    font-size: 16px;
    cursor: pointer;
}

.overlay .title:hover{
    color: #fff;
}

.overlay .detail {
    color: #fff;
    font-size: 14px;
    margin-top: 10px;
}
    

</style>