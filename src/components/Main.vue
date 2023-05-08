<script>
import SingleCard from './SingleCard.vue'
import {store} from '../store';

export default{
  name: "Main",
  components:{
    SingleCard
  },
  data(){
    return{
      store
    }
},
}
</script>

<template>
    <main>
        <div id="select" class="container">
            <select name="" v-model="store.selectValue" @click.prevent="$emit('selectEmit')">
                <option value="" disabled>--Cerca per Archetipo--</option>
                <option :value="elem.archetype_name" v-for="(elem, index) in store.archetypeArray" :key="index">{{ elem.archetype_name }}</option>
            </select>
        </div>
        
        <div id="box-orange" class="container">
            
            <div id="box-white" class="container">
                <div id="banner"> 
                   <div class="ps-3">Card found: {{ store.arrayCarte.length }}</div> 
                </div>    
                <div id="cards-box" class="row container">
                    <SingleCard 
                        v-for="(elem, index) in store.arrayCarte" 
                        :key="index"
                        :infoCard="elem"
                    />
                </div>
            </div> 
        </div>
    </main>
</template>

<style lang="scss" scoped>
main{
    background-color: #D48F38;
    height: calc(100vh - 100px);
    overflow-y: auto;
    display: grid;
    place-items: center;
    padding-top: 100px;
    #select{
        padding: 0;
        margin-bottom: 30px;
    }
    #box-orange{
        background-color: white;
        display: grid;
        place-items: center;
        
        #box-white{
            
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            #banner{
                background-color: #0E0E0E;
                width: 100%;
                margin-top: 50px;
                height: 50px;
                display: flex;
                align-items: center;
                color: white;
            }
            #cards-box{
                background-color: white;
                margin-bottom: 50px;
                justify-content: space-between;
                padding: 0;
                
            }
        }     
    }
}
</style>
