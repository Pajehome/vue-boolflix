<template>
  <div>
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

     
    <section id="section1">
      <a href="#section3" class="arrow__btn left-arrow">‹</a>
      <div class="item">
        <a href="#">
          <img :src="images + item.backdrop_path" alt="" />
             <h1 class="heading">{{ item.title ? item.title : item.name }}</h1>
            <p class="duration">
              <span v-for="(numero, index) in 5" :key="index">
               <i
              :class="
                numero <= rounds(item.vote_average)
                  ? 'fa-solid fa-star yellow'
                  : 'fa-solid fa-star'">
               </i>
             </span>
             <country-flag :country="item.original_language" size="small" /> 
            </p> 
          
       </a>
     </div>
     <a href="#section1" class="arrow__btn right-arrow">›</a>
    </section> 
    
   </div> 
</template>

<script>
//import CountryFlag from "vue-country-flag";
export default {
  name: "CardComponent",
  components: {
    //CountryFlag,
  },
  data() {
    return {};
  },
  props: {
    item: Object,
    images: String,
  },
  methods: {
    rounds(txt) {
      return Math.round(txt / 2);
    },
  },
};
</script>

<style lang="scss">

  section {
    width: 100% !important;
    position: relative !important;
    display: grid !important;
    grid-template-columns: repeat(5, auto) !important;
    margin: 20px 0 !important;
    
    .item {
      position: relative;
      padding: 0 2px;
      transition: 250ms all;
      
      &:hover { 
        margin: 0 40px;
        transform: scale(1.2);
      }


      .heading {
        position: absolute;
        bottom: 20px;
        left: 20px;
        color: #fff;
      }

      .duration {
        position: absolute;
        bottom: 0;
        left: 20px;
        color: #fff;
      }
      
    }

    .arrow__btn {
      position: absolute;
      color: #fff;
      text-decoration: none;
      font-size: 6em;
      background:rgb(0,0,0);
      width: 80px;
      padding: 20px;
      text-align: center;
      z-index: 1;
    }

    .left-arrow {
      top:0; bottom:0; left:0;
      background: linear-gradient(-90deg, rgba(0,0,0,0) 0%, rgba(0,0,0,1) 100%);
    }
    
    .right-arrow {
      top:0; bottom:0; right: 0;
      background: linear-gradient(90deg, rgba(0,0,0,0) 0%, rgba(0,0,0,1) 100%);
    }

  }
</style>