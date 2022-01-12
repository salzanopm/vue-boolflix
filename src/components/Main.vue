<template>
    <main>
        <h2>FILM</h2>
        <!-- su key uso o index o un identificativo tipo ID in questo caso -->
        <MovieCard v-for="movie in moviesList" :key="movie.id" :details="movie" />
    </main>
</template>

<script>
import MovieCard from './MovieCard.vue';
export default {
    name: 'Main',
    components: {
        MovieCard
    },
    props: {
        moviesList: Array,
    }
}
</script>