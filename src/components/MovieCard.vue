<template>
<div>
    <div>
        <img :src="`https://image.tmdb.org/t/p/${imgWidthMovie}${details.poster_path}`" alt="">
    </div>
    <div class="movie">
        <div>Titolo: {{details.title}}</div>
        <div>Titolo originale: {{details.original_title}}</div>
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
            imgWidthMovie: 'w342'
        }

    }
}
</script>

<style scoped>
.movie {
    margin: 20px;
    border: 2px solid black;
}

.img-language {
    width: 10px;
}
</style>