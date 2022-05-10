<template>
  <div>
    <SearchComponent :movieProp="movies" @search="mySearch"/>
   <div v-for="(tito, index) in filteredSearch" :key='index'>
     <h1>{{tito.title}}</h1>
     <h2>{{tito.original_title}}</h2>
     <h3>{{tito.original_language}}</h3>
     <h4>{{tito.vote_average}}</h4>
   </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchComponent from './SearchComponent.vue';

export default {
 name: 'MainComponent',
 components:{
    SearchComponent,
 },
  data(){
    return {
      movies:[],
      searchText: '',
    }
  },
  methods:{
      mySearch(txt){
          this.searchText = txt;
      },
  },
  computed:{
          filteredSearch(){
          return this.movies.filter((item) => {
          return item.title === this.searchText;
        })
        }
  },
  mounted() {
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro').then((res) => {
      console.log(res.data.results);
      this.movies = res.data.results;
      console.log(this.movie)
    }).catch((err) => {
        console.log(err)
    })
  }
}
</script>

<style lang="scss">

</style>