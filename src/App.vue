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
      apiPath:'https://api.themoviedb.org/3/search/movie/?api_key=c13f1efdfd69df15ca0fe5b05aab0175&query='
    }
  },
  methods:{
    searchMovie(){
      let transformedTitle=this.inputText.split(' ').join('+');
      console.log(transformedTitle);
      axios.get(this.apiPath+transformedTitle+'&language=it-IT').then((res)=>{
          console.log(res)
        }).catch((error)=>{
          console.log(error)
        })
    }
  },
}

</script>

<style lang="scss">
@import './style/general.scss';

</style>
