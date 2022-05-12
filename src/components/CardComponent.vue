<template>
  <div>
      
         <li>
          id: {{item.id}}<br />
          titolo originale: {{item.original_title ? item.original_title : item.original_name}}<br />
          titolo: {{item.title ? item.title : item.name}}<br />
          lingua: {{item.original_language}}<br />
         <country-flag :country='item.original_language' size='small'/> <br />
          voto: {{rounds(item.vote_average)}}
          <img :src="image+item.backdrop_path" alt="">
          <span v-for="(numero, index) in 5" :key="index">
              <i :class="numero <= rounds(item.vote_average) ? 'fa-solid fa-star yellow' : 'fa-solid fa-star'"></i>
          </span>
        </li>
      
  </div>
</template>

<script>
 import CountryFlag from 'vue-country-flag'
export default {
name: 'CardComponent',
 components:{
      CountryFlag,
    },
data(){

},
props:{
        item: Object,
        images: String,
        
    },
 methods:{
   rounds(txt){
           return   Math.round(txt / 2)   
       }
 }   
}
</script>

<style>

</style>