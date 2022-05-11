<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-12">
          <div class="input-group my-3">
            <input type="text" class="form-control" placeholder="Cerca Per Titolo" v-model="inputText" aria-label="Recipient's username" aria-describedby="button-addon2">
            <button @click="searchMovie()" class="btn btn-outline-secondary" type="button" id="button-addon2">Cerca</button>
          </div>
        </div>
        <div class="border d-block" v-for="(film,index) in filmSpecifics" :key="index">
          <span>{{'Titolo:'+' '+film.title}}</span>
          <span>{{'Titolo in lingua originale:'+' '+film.original_title}}</span> 
          <span>Lingue: <flag :iso="language(film)"/></span>   
          <span>{{'Voto:'+' '+film.vote_average}}</span> 
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';


export default{
  name:'app',
  data(){
    return {
      inputText:'',
      apiKey:'c13f1efdfd69df15ca0fe5b05aab0175',
      apiPath:'https://api.themoviedb.org/3/search/',
      filmSpecifics:[],
    }
  },
  methods:{
    searchMovie(){
      let transformedTitle=this.inputText.split(' ').join('+');
      console.log(transformedTitle);
      const queryParams ={
        params:{
          api_key:this.apiKey,
          query:transformedTitle,
          language:'it-IT',
        }
      }
      axios.get(this.apiPath+'movie',queryParams).then((res)=>{
          this.filmSpecifics = res.data.results;
          console.log(this.filmSpecifics)
      }).catch((error)=>{
          console.log(error)
      })
    },
    language(film){
      if(film.original_language === 'en'){
        return film.original_language = 'gb'
      }else if(film.original_language === 'ja'){
        return film.original_language = 'jp'
      }else{
        return film.original_language
      }
    }
  },
}

</script>

<style lang="scss">
@import './style/general.scss';
span{
  margin-right: 4%;
}

</style>
