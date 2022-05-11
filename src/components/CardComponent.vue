<template>
  <div>
      <ul>
         <li>
          id: {{item.id}}<br />
          titolo originale: {{item.original_title ? item.original_title : item.original_name}}<br />

          titolo: {{item.title ? item.title : item.name}}<br />

          lingua: {{item.original_language}}<br />

          <country-flag :country='item.original_language' size='small'/> <br /> 

          voto: {{item.vote_average}}<br />

          <img :src="imagee+item.backdrop_path" alt="">
        </li>
      </ul>
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
        item: Array,
        loaderr: Boolean,
        titlee: String,
        imagee: String,
        
    },
}
</script>

<style>

</style>