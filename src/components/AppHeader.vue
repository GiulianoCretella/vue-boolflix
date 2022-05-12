<template>
<div class="container">
 <section class="row align-items-center">
      <div class="col-6 g-0">
          <span class="logo">boolflix <i class="fa-regular fa-registered"></i></span>
      </div>
    <search-bar @search="search"/>
  </section>
</div>
</template>

<script>
import {state} from '../store.js'
import axios from 'axios';
import SearchBar from './SearchBar.vue';
export default {
    name:'AppHeader',
    components:{
        SearchBar,
    },
    data(){
        return{
            apiKey:'c13f1efdfd69df15ca0fe5b05aab0175',
            apiPath:'https://api.themoviedb.org/3/search/',
            seriesSpecifics:[],
            movieSpecifics:[],
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
      
    },
    searchSeries(queryParams){
       axios.get(this.apiPath+'tv',queryParams).then((res)=>{
          this.seriesSpecifics = res.data.results;
          console.log(this.seriesSpecifics)
          state.finalSearch= [...this.seriesSpecifics,...this.movieSpecifics]
      }).catch((error)=>{
          console.log(error)
      })

    },
    searchMovies(queryParams){
      axios.get(this.apiPath+'movie',queryParams).then((res)=>{
          this.movieSpecifics = res.data.results;
          console.log(this.movieSpecifics)
          state.finalSearch= [...this.seriesSpecifics,...this.movieSpecifics]
      }).catch((error)=>{
          console.log(error)
      })
    },
   
  },
}
</script>

<style lang="scss" scoped>

.logo{
   font-size: 50px;
   -webkit-text-stroke: 1px rgb(35, 0, 0);
   text-shadow: 4px 0.5px 2px rgb(38, 2, 2);
   color: rgb(255, 6, 6);
   font-weight:bold;
   font-family: 'Koulen', 'cursive';
}
.fa-registered{
    font-size: 15px;
    color: white; 
    -webkit-text-stroke: 0.2px black;
    text-shadow: none;
    position: relative;
    top: -25px;
    left: -5px;
}
</style>