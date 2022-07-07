<template>
  <div id="app">
    <header class="d-flex justify-content-around pt-3">
       <h1>Boolflix</h1>
       <search-component @performSearch="search" />
    </header>
    <main>    
      
     <div v-if="home">
        <home-component/>
      </div> 
      
     <div v-if="main">
          <main-component :items="movies"  :loader="loading" :image="tmdbImage"  :title="title == true ? 'Movies'  : ''"/>
          <main-component :items="series"  :loader="loadingSeries" :image="tmdbImage" :title="title == true ? 'Series'  : ''" />
     </div>
     

    </main>
   
  </div>
</template>

<script>
import MainComponent from './components/MainComponent.vue'
import SearchComponent from './components/SearchComponent.vue'
import HomeComponent from './components/HomeComponent.vue'

import axios from 'axios'
export default {
  name: 'App',
  components: {
    SearchComponent,
    MainComponent,
    HomeComponent,
  },
  data(){
    return{
      apiKey: 'e99307154c6dfb0b4750f6603256716d',
      apiPath: 'https://api.themoviedb.org/3/search/',
      movies:[],
      series:[],
      loading: false,
      loadingSeries: false,
      title: false,
      tmdbImage: 'https://image.tmdb.org/t/p/w342',
      home: true,
      main: false,
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
      this.home = false,
      this.main = true,
      this.title = true;
      this.loading = true;
      this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
    },
  },
 }
</script>

<style lang="scss">
  @import './assets/styles/general.scss';
  header{
    background-color:$header-background;
    h1{
       font-weight: bold;
       text-transform: uppercase;
       line-height: 32px;
    }
  }
  main{
    font-weight: bold;
    text-transform: uppercase;
  }
</style>