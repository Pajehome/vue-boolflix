<template>
    <div>
      <input type="text" v-model="inputText" @keyup.enter="$emit('performSearch',inputText)">
      <button @click="cerca">Cerca</button>
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

</style>