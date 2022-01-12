<template>

    <section>
        <div class="container d-flex justify-content-center"> 

            <div class="row row-cols-2 row-cols-lg-5">

                <ul v-for = "(element, index) in movies" :key='index'>
                    <li>{{ element.title }}</li>
                    <li>{{ element.original_title }}</li>
                    <li>{{ element.original_language }}</li>
                    <li>{{ element.vote_average }}</li>   
                </ul>  
            </div>

        </div>    
    </section>
    
</template>

<script>
export default {
    name: 'Main',
    
    props: {
        movies: Array,
    },
}
</script>

<style lang="scss" scoped>

section {
    margin-top: 30px;
    

    ul{ 
        margin: 5px;      
        width: 250px;
        text-align: center;
        padding: 30px;
        border: 3px solid black;

        li {
            list-style-type: none;
        }
    }
}
</style>