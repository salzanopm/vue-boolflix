<template>
    <div>
        <div>
            <img :src="`https://image.tmdb.org/t/p/${imgWidth}${details.poster_path}`" alt="">
        </div>
        <div class="movie">
            <div>Titolo: {{details.title}}</div>
            <div>Titolo originale: {{details.original_title}}</div>
            <!-- se bandiera inclusa in array, usa immagine `-->
            <div v-if="flagList.includes(details.original_language)">
                Lingua:
                <img :src="require(`../assets/${details.original_language}.png`)" class="img-language" alt="">
            </div>
            <!-- altrimenti stampa normalmente -->
            <div v-else>
                Lingua: {{details.original_language}}
            </div>
            <div>Voto: {{details.vote_average}}</div>
        </div>
</div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        details: Object
    },
    data: function() {
        return {
            flagList: ['it','en'],
            imgWidth: 'w500'
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