<template>
  <div id="app">
    <header>
       <h1 class="display-6">Boolflix</h1>
       <search-component @performSearch="search" />
    </header>
    <main>     
      <main-component :items="movies" title="Movies" :loader="loading" :image="tmdbImage"/>
      <main-component :items="series" title="Series" :loader="loadingSeries" :image="tmdbImage"/>
    </main>
   
  </div>
</template>

<script>
import MainComponent from './components/MainComponent.vue'
import SearchComponent from './components/SearchComponent.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    SearchComponent,
    MainComponent,
  },
  data(){
    return{
      apiKey: 'e99307154c6dfb0b4750f6603256716d',
      apiPath: 'https://api.themoviedb.org/3/search/',
      movies:[],
      series:[],
      loading: false,
      loadingSeries: false,
      tmdbImage: 'https://image.tmdb.org/t/p/w342',
    }
  },
  methods:{
    getMovies(queryParams){
      axios.get(this.apiPath+'movie', queryParams).then((res)=>{
        this.movies = res.data.results;
        this.loading = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    getSeries(queryParams){
      axios.get(this.apiPath+'tv', queryParams).then((res)=>{
        this.series = res.data.results;
        this.loadingSeries = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    search(text){
       const queryParams = {
        params:{
          api_key: this.apiKey,
          query: text
        }
      }
      this.loading = true;
      this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    }
  }
 }
</script>

<style lang="scss">
  @import './assets/styles/general.scss' 
</style>