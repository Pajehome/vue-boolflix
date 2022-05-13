<template>
  <div class="box">
    
    <!-- <div class="card  cio" style="width: 18rem">
      <img :src="images + item.backdrop_path" alt="" />
      <div class="card-body">
        <p class="card-text">
          id: {{ item.id }}<br />
          titolo originale:
          {{ item.original_title ? item.original_title : item.original_name
          }}<br />
          titolo: {{ item.title ? item.title : item.name }}<br />
          lingua: {{ item.original_language }}<br />
          <country-flag :country="item.original_language" size="small" /> <br />
          voto: {{ rounds(item.vote_average) }}

          <span v-for="(numero, index) in 5" :key="index">
            <i
              :class="
                numero <= rounds(item.vote_average)
                  ? 'fa-solid fa-star yellow'
                  : 'fa-solid fa-star'">
            </i>
          </span>
        </p>
      </div>
    </div> -->

     
  
      <a :href="'#'[currentIndex]" class="arrow__btn left-arrow" @click="prevSlide">‹</a>
      <a :href="'#'[currentIndex]" class="arrow__btn right-arrow" @click="nextSlide">‹</a>

      <div class="item">

       <a :href="'#'[currentIndex]">

          <div class="immagine">
             <img :src="images + item.backdrop_path" alt="" />
          </div>
          
          <div class="over">
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
       </a>
      </div> 
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
      currentIndex: 0,
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
   
    nextSlide(){
           if(this.currentIndex >= this.itemss.length -1){
             this.currentIndex = 0
           }else{
             this.currentIndex++
           }
          },    
          prevSlide(){
            if(this.currentIndex <= 0){
                this.currentIndex = this.itemss.length -1
                
            }else{
             this.currentIndex--
            }
          },
  },
};
</script>

<style lang="scss" scoped>

  
    .box{
     height: 192px;
     width: 342px;
     
     .item {
       position: relative;
       padding: 0 2px;
    //   transition: 250ms all;
      
    //   &:hover { 
    //     margin: 0 40px;
    //     transform: scale(1.2);
    //   };

      .immagine{
        display: block;
        z-index: 2;
        position: absolute;
        top: 0;
        left: 0;
        
        &:hover{
          display: none;
        }
      }
      .over{
        display: block;
        height: 192px;
        position: absolute;
        padding: 0 2px;
        transition: 250ms all;
        background-color: black;
        top: 0;
        left: 0;
        contain: content;
        overflow-y: auto;
        z-index: 0;

      }
      h5{
        display: inline-block;
      }
    } 
  

    .arrow__btn {
      position: absolute;
      color: #fff;
      text-decoration: none;
      font-size: 6em;
      width: 80px;
      padding: 20px;
      text-align: center;
      z-index: 1;
    }

    .left-arrow {
      top:0; bottom:0; left:0;
      
    }
    
    .right-arrow {
      top:0; bottom:0; right: 0;
      
    }
    } 

</style>