<template>
  <div id="app">
    <!-- evento che ascolto dal figlio -->
    <Header @searchDone="search" />
    <Main :moviesList="moviesArray" :seriesList="seriesArray"/>
  </div>
</template>

<script>
// importo axios per chiamata api (dopo aver fatto npm install axios)
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
export default {
  name: "App",
  components: {
    Header,
    Main
  },
  data: function() {
    return {
      queryValue: '',
      apiKey: 'a0b682908621022f4b52c032dae08e99',
      moviesArray: [],
      seriesArray: []
    }
  },
  methods: {
    search: function(userString) {
      this.queryValue = userString;
      this.getMovies();
      this.getSeries();
    },
    // funzione chiamata API
    getMovies: function() {
      axios.get(
        // richiesta API
        'https://api.themoviedb.org/3/search/movie',
        {
          //dentro richiesta API mettiamo i parametri della chiamata in un oggetto
          params: {
            api_key: this.apiKey, // variabilizzata in data 
            query: this.queryValue, // variabilizzata in data 
          }
        }
      // seconda parte richiesta API
      ).then((response) => {
        // popolo il mio array con i risultati dell'API
        this.moviesArray = response.data.results
      }); 
    },
    getSeries: function() {
      axios.get(
        // richiesta API
        'https://api.themoviedb.org/3/search/tv',
        {
          //dentro richiesta API mettiamo i parametri della chiamata in un oggetto
          params: {
            api_key: this.apiKey, // variabilizzata in data 
            query: this.queryValue, // variabilizzata in data 
          }
        }
      // seconda parte richiesta API
      ).then((response) => {
        // popolo il mio array con i risultati dell'API
        this.seriesArray = response.data.results
      }); 
    }
  }
} 
</script>

<style>

</style>
