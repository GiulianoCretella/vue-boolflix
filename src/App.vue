<template>
  <div id="app">
    <div class="container">
      <search-bar @search="search"/>
      <div class="row">
        <h1>boolFix</h1>
        <div class="col-2 border" v-for="(film,index) in filmSpecifics" :key="index">
          <app-grid :item="film"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue';
import AppGrid from './components/AppGrid.vue';


export default{
  components: {
    SearchBar,
    AppGrid 
  },
  name:'app',
  data(){
    return {
      apiKey:'c13f1efdfd69df15ca0fe5b05aab0175',
      apiPath:'https://api.themoviedb.org/3/search/',
      seriesSpecifics:[],
      movieSpecifics:[],
      filmSpecifics:[],
      film:''
    }
  },
  methods:{
    search(val){
      this.film= val;
      const queryParams ={
        params:{
          api_key:this.apiKey,
          query:this.film,
          language:'it-IT',
        }
      }
      this.searchSeries(queryParams);
      this.searchMovies(queryParams);
      this.filmSpecifics=[...this.seriesSpecifics,...this.movieSpecifics]
    },
    searchSeries(queryParams){
       axios.get(this.apiPath+'tv',queryParams).then((res)=>{
          this.seriesSpecifics=[...res.data.results];
          console.log(this.seriesSpecifics)
      }).catch((error)=>{
          console.log(error)
      })
    },
    searchMovies(queryParams){
      axios.get(this.apiPath+'movie',queryParams).then((res)=>{
          this.movieSpecifics=[...res.data.results];
          console.log(this.movieSpecifics)
      }).catch((error)=>{
          console.log(error)
      })
    },
   
  },
}

</script>

<style lang="scss">
@import './style/general.scss';
h1{
  font-size: 100px;
  -webkit-text-stroke: 1px red;
   text-shadow: 3px 0 2px red;
}
span{
  margin-right: 4%;
}

</style>
