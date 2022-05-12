<template>
    <section>
        <h2>{{title}}</h2>
        <div class="wrapper">
          <card-component v-for ='(card, index) in items'  :key="index" :item='card' :images='image'/>
        </div>
        
       <!-- <ul>
         <li v-for="(item) in items" :key="item.id">
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
      </ul>  -->
     
    </section>
</template>

<script>

import CardComponent from './CardComponent.vue'
export default {
    name: 'MainComponent', 
    components:{
    CardComponent,
    },
    props:{
        items: Array,
        loader: Boolean,
        title: String,
        image: String,
    },
    data(){
        return {
            
        }
    },
    computed: {
       
    },
    methods:{
        
       },
}
</script>

<style lang="scss">
.wrapper {
  display: grid !important;
  grid-template-columns: repeat(3,100%)!important;
  overflow:hidden !important;
  scroll-behavior: smooth !important;
}  

.yellow{
   color: yellow;
}
</style>