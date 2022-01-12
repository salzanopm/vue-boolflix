<template>
    <main>
        <h2>FILM</h2>
        <!-- su key uso o index o un identificativo tipo ID in questo caso -->
        <MovieCard v-for="movie in moviesList" :key="movie.id" :details="movie" />
        <h2>SERIE TV</h2>
        <SeriesCard v-for="series in seriesList" :key="series.id" :details="series" />
    </main>
</template>

<script>
import SeriesCard from './SeriesCard.vue';
import MovieCard from './MovieCard.vue';
export default {
    name: 'Main',
    components: {
        MovieCard,
        SeriesCard
    },
    props: {
        moviesList: Array,
        seriesList: Array,
    }
}
</script>