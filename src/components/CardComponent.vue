<template>
  <div>
      
         <li>
          id: {{card.id}}<br />
          titolo originale: {{card.original_title ? card.original_title : card.original_name}}<br />
          titolo: {{card.title ? card.title : card.name}}<br />
          lingua: {{card.original_language}}<br />
         <country-flag :country='card.original_language' size='small'/> <br />
          voto: {{rounds(card.vote_average)}}
          <img :src="image+card.backdrop_path" alt="">
          <span v-for="(numero, index) in 5" :key="index">
              <i :class="numero <= rounds(card.vote_average) ? 'fa-solid fa-star yellow' : 'fa-solid fa-star'"></i>
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
        card: Object,
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