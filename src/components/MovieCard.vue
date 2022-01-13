<template>
<div class="cont">
    
    <div  class="img-container"  >
        <img class="img-card" :src="`https://image.tmdb.org/t/p/${imgWidthMovie}${details.poster_path}`" alt="">
    </div>
    <div class="info-container">
        <div>Titolo: {{details.title}} {{details.name}} </div>
        <div>Titolo originale: {{details.original_title}} {{details.original_name}}</div>
        <!-- se bandiera inclusa in array, usa immagine `-->
        <div v-if="flagListMovie.includes(details.original_language)">
            Lingua:
            <img :src="require(`../assets/${details.original_language}.png`)" class="img-language" alt="">
        </div>
        <!-- altrimenti stampa normalmente -->
        <div v-else>
            Lingua: {{details.original_language}}
        </div>
        <div>
            Voto:
            <i class="fas fa-star" v-for="number,index in getNumberOfStars(details.vote_average)" :key='index'></i>
            <i class="far fa-star" v-for="number,index in (5 - getNumberOfStars(details.vote_average))" :key='index'></i>
        <!-- <div>Voto: {{details.vote_average}}</div> -->
        </div>
        <div>
            Lingua: {{details.overview}}
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        details: Object
    },
    methods: {
        getNumberOfStars: function(vote) {
            return Math.ceil(vote/2);
        }
        
    },
    data: function() {
        return {
            flagListMovie: ['it','en'],
            imgWidthMovie: 'w342',
            value1: true,
            value2: false
        }
    }
}

  
   

</script>

<style scoped lang="scss">
.fas.fa-star {
    color: rgb(245, 224, 39);
}
.img-container {
    width: 342px;
    height: 658px;
    margin: 20px;
    img {
        width: 100%;
        height: 100%;
    }
}

.info-container {
    width: 342px;
    height: 658px;
    margin: 20px;
    display: none;
    border: 1px solid black;
    padding: 20px;
    background-color: rgba(80, 80, 80, 0.6);
    color: white;
}

.cont:hover .img-container{
    display: none;

}
.cont:hover .info-container{
    display: block;
}

.img-language {
    width: 15px;
}
</style>

