<template>
  <div class="container">
    <div class="input-group mb-3">
       <input type="text" class="form-control" placeholder="Cerca Film" aria-describedby="button-addon2" v-model="inputText" @keyup="searchMovie">
       <button class="btn btn-outline-secondary" type="button" id="button-addon2" @click="searchMovie">Button</button>
    </div>
    <ul>
      <li v-for="(movie, index) in movieProp" :key="index">{{movie.title}}</li>
    </ul>
  </div>
</template>

<script>
export default {
name: 'SearchComponent',
data(){
  return{
    inputText: ''
  }
},
props:['movieProp'],
methods: {
 searchMovie(){
   this.$emit('search', this.inputText)
 } 
}
}

</script>

<style lang='scss'>

</style>