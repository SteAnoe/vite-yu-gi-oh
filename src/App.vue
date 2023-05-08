<script>
import axios from 'axios';
import {store} from './store';
import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default{
  name: "App",
  components: {
    Header,
    Main
  },
  data(){
    return{
      store
    }
  },
  created(){
    this.apiCall
    this.archetypeCall()
  },
  computed:{
    apiCall(){
      if ( store.selectValue !== ''){
        axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${store.selectValue}`)
        .then( (res) =>{
          const apiData = res.data.data
          this.store.arrayCarte = apiData
        })
      }else {
        
      }
    }
  },
  methods: {
    archetypeCall(){
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
       .then( (res) =>{
        this.store.archetypeArray = res.data
       })
    },
    
  }
}

</script>

<template>
  <Header/> 
  <Main @selectEmit="apiCall"/>
</template>

<style lang="scss">
@use "./style/main.scss" as *;
</style>
