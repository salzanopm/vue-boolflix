<template>
    <div class="series">
        <div>Titolo: {{details.name}}</div>
        <div>Titolo originale: {{details.original_name}}</div>
        <!-- se bandiera inclusa in array, usa immagine -->
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

</template>

<script>
export default {
    name: 'SeriesCard',
    props: {
        details: Object
    },
    data: function() {
        return {
            flagList: ['it','en']
        }
    }
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