<template>
  <div id="app">
    <header>
      <app-header/>
    </header>
    <div class="container">
      <div class="row">
        <div class="col-3 border" v-for="(film,index) in finalSearch" :key="index">
          <app-grid :item="film"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import{state} from './store.js';
import AppGrid from './components/AppGrid.vue';
import AppHeader from './components/AppHeader.vue';


export default{
  name:'app',
  components: {
    AppGrid ,
    AppHeader,
  },
  data(){
    return {
      
    }
  },
  computed:{
    finalSearch(){
      return state.finalSearch;
    }
  },
  methods:{
    
  }
}

</script>

<style lang="scss">
@import './style/general.scss';
header{
  background-color: $bg_header;
}
span{
  margin-right: 4%;
}

</style>
