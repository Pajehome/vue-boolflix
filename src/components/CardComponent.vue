<template>
       <div class="item ">
            <div class="immagine" v-if="hover" @mouseover='hover = false' >
                <img :src="images + item.backdrop_path" @error="setAltImg" alt=""  />
            </div>
          
            <div class="over" @mouseleave='hover = true'>
                <div>
                   <h5>Titolo:</h5> <span>{{ item.title ? item.title : item.name }}</span>
                </div>

                <div>
                   <h5>Titolo Originale:</h5> <span>{{item.original_title ? item.original_title : item.original_name }}</span>
                </div>
             
                <div>
                  <h5>
                   Voto:
                  <span v-for="(numero, index) in 5" :key="index">
                     <i
                       :class="
                        numero <= rounds(item.vote_average)
                        ? 'fa-solid fa-star yellow'
                        : 'fa-solid fa-star'">
                     </i>
                  </span>
                  </h5>
                </div> 
             
                <div>
                  <h5>Overview:</h5> <span>{{item.overview}}</span>
                </div>
 
                <country-flag :country="item.original_language" size="small" />    
             </div> 
             <h6 class="my-2 text-center text-white" v-if="item.title">{{item.title}}</h6>
             <h6 class="my-2 text-center text-white" v-if="item.name">{{item.name}}</h6>
         </div> 
</template>

<script>
import CountryFlag from "vue-country-flag";


export default {
  name: "CardComponent",
  components: {
    CountryFlag,
   
  },
  data() {
    return {
      hover: true,
    };
  },
  props: {
    itemss: Array,
    item: Object,
    images: String,
    indice: Number,
  },
  methods: {
    rounds(txt) {
      return Math.round(txt / 2);
    },
    setAltImg(event) { 
    event.target.src = "boolflixx.png.png" 
}
  },
};
</script>

<style lang="scss">
 
    .item{
     width: 342px !important;
     height: 192px;
     
      .immagine{
      position: absolute; 
       z-index: 1;
       background-color: black;
       width: 342px;
       height: 192px;

       img{
         width: 100%;
         height: 100%;
         object-fit: contain;
       }
      }
      .over{
       contain: content;
       overflow-y: scroll;
       overflow-x: hidden;
       height: 100%;
       width: 342px;
       font-size: 0.85rem;
       background: #000000;
       color: #fff;
       opacity: 0.75;
       padding: 8px;
       
          h5{
            font-size: 1rem; 
            display: inline-block;
            color: #bf5b5b;
          }

          .fa-star{
            color: #fff;
          }

        }
      ::-webkit-scrollbar {
          width: 0.5em;
          }

      ::-webkit-scrollbar-thumb {
      background-color: rgb(63, 62, 62);
      outline: 1px solid rgb(48, 50, 52);
      border-radius: 10px;
      }
            }

</style>