<template>
    <section>
        <h2>{{title}}</h2>
       <ul>
        <li v-for="(item) in items" :key="item.id">
          id: {{item.id}}<br />
          titolo originale: {{item.original_title ? item.original_title : item.original_name}}<br />
          titolo: {{item.title ? item.title : item.name}}<br />
          lingua: {{item.original_language}}<br />
         <country-flag :country='item.original_language' size='small'/> <br />
          voto: {{item.vote_average}}<br />
        </li>
      </ul>
     
    </section>
</template>

<script>
import CountryFlag from 'vue-country-flag'

export default {
    name: 'MainComponent',
    components:{
     CountryFlag,
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
      
    }
}
</script>

<style lang="scss">

</style>