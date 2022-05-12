<template>
<div class="container">
    <div class="row">
        <div class="col-sm-6 col-md-3 col-xl-2" v-for="(film,index) in finalSearch" :key="index">
          <main-card :item="film"/>
        </div>
    </div>
</div>
   
</template>

<script>
import{state} from '../store.js';
import MainCard from './MainCard.vue'
export default {
    name:'AppGrid',  
    components: {
       MainCard 
    },
    computed:{
    finalSearch(){
      return state.finalSearch;
    }
  },
}
</script>

<style lang="scss">

</style>