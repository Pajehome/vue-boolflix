<template>
    <section>
        <h2 class="container pt-2 mb-5" >{{title}}</h2>
        <div class="container-fluid">
           <section class="row">
               <card-component v-for ='(card, index) in items'  :key="index" :item='card' :itemss='items' :images='image' :indice='index'/>
           </section> 
        </div> 
    </section>
</template>

<script>

import CardComponent from './CardComponent.vue';


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
            value: this.value === this.items.length
        }
    },
    computed: {
       
    },
    methods:{
        
       },
}
</script>

<style lang="scss">
.yellow{
   color: yellow !important;
}

.row{
    justify-content: center;
    gap: 3rem;
    height: 100%;
    position: relative;
    padding: 10px;
}

</style>