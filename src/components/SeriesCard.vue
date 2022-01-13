<template>
<div>
    <div>
        <img :src="`https://image.tmdb.org/t/p/${imgwidthSeries}${details.poster_path}`" alt="">
    </div>
    <div class="series">
        <div>Titolo: {{details.name}}</div>
        <div>Titolo originale: {{details.original_name}}</div>
        <!-- se bandiera inclusa in array, usa immagine -->
        <div v-if="flagListSeries.includes(details.original_language)">
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
    name: 'SeriesCard',
    props: {
        details: Object
    },
    data: function() {
        return {
            flagListSeries: ['it','en'],
            imgwidthSeries: 'w342'
        }
    },
    methods: {
        getNumberOfStars: function(vote) {
            return Math.ceil(vote/2);
        }
        
    },
   
}
</script>

<style scoped>
.series {
    margin: 20px;
    border: 2px solid black;
}

.img-language {
    width: 10px;
}
</style>