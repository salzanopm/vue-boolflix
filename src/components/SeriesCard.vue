<template>
    <div class="series">
        <div>Titolo: {{details.name}}</div>
        <div>Titolo originale: {{details.original_name}}</div>
        <div>Lingua: {{details.original_language}}</div>
        <div>Voto: {{details.vote_average}}</div>
    </div>

</template>

<script>
export default {
    name: 'SeriesCard',
    props: {
        details: Object
    }
}
</script>

<style scoped>
.series {
    margin: 20px;
    border: 2px solid black;
}
</style>