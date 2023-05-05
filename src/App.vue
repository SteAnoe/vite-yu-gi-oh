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
    this.apiCall()
  },
  methods: {
    apiCall(){
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=Alien')
        .then( (res) =>{
          
          const apiData = res.data.data
          this.store.arrayCarte = apiData
          console.log(apiData)
        })
    }
  }
}

</script>

<template>
  <Header/> 
  <Main/>
</template>

<style lang="scss">
@use "./style/main.scss" as *;
</style>
