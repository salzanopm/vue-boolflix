<template>
    <main>
        
        <h2>FILM</h2>
        <div class="card-container">
            <!-- su key uso o index o un identificativo tipo ID in questo caso -->
            <MovieCard v-for="movie in moviesList" :key="movie.id" :details="movie" />
        </div>
        <h2>SERIE TV</h2>
        <div class="card-container">
            <MovieCard v-for="series in seriesList" :key="series.id" :details="series" />
        </div>
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
        seriesList: Array
    }
}
</script>

<style lang="scss" scoped>
main {
    background-color: black;
    height: calc(100vh - 130px);
}
.card-container {
    display: flex;
    overflow-x: auto;
    background-color: black;
}

h2 {
    background-color: black;
    
}
</style>