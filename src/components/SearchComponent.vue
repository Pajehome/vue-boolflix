<template>
    <!-- <div>
      <input type="text" v-model="inputText" @keyup.enter="$emit('performSearch',inputText)">
      <button @click="cerca">Cerca</button>
    </div> -->

      <div class="search-box mb-3">
    <button class="btn-search"><i class="fas fa-search"></i></button>
    <input type="text" class="input-search" placeholder="Type to Search..." v-model="inputText" @keyup.enter.prevent="$emit('performSearch',inputText)">
    </div>
</template>

<script>
export default {
    name: 'SearchComponent',
    data(){
        return {
           inputText:'' 
        }
    },
    computed:{
    },
    methods:{
        cerca(){
            this.$emit('performSearch',this.inputText)
            this.inputText = ''
        }
    }
}
</script>

<style lang="scss">

.search-box{
  width: fit-content;
  height: fit-content;
  position: relative;
}
.input-search{
  height: 40px;
  width: 40px;
  border-style: none;
  padding: 10px;
  font-size: 15px;
  letter-spacing: 2px;
  outline: none;
  border-radius: 25px;
  transition: all .5s ease-in-out;
  background-color: #E50914;
  padding-right: 31px;
  color:#fff;
}
.input-search::placeholder{
  color:rgba(255,255,255,.5);
  font-size: 18px;
  letter-spacing: 2px;
  font-weight: 100;
}
.btn-search{
  width: 42px;
  height: 44px;
  border-style: none;
  font-size: 18px;
  font-weight: bold;
  outline: none;
  cursor: pointer;
  border-radius: 50%;
  position: absolute;
  right: 0px;
  color: #000;;
  background-color:transparent;
  pointer-events: painted;  
}
.btn-search:focus ~ .input-search{
  width: 300px;
  border-radius: 0px;
  background-color: transparent;
  border-bottom:1px solid rgba(255,255,255,.5);
  transition: all 500ms cubic-bezier(0, 0.110, 0.35, 2);
}
.input-search:focus{
  width: 300px;
  border-radius: 0px;
  background-color: transparent;
  border-bottom:1px solid rgba(255,255,255,.5);
  transition: all 500ms cubic-bezier(0, 0.110, 0.35, 2);
}

</style>