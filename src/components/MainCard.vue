<template>
  <div class="poster-container align-items-center">
    <img class="img-fluid h-100 w-100" :src="image + imageFunc" alt="">
    <!-- <div>{{'Titolo:'+' '+[item.title ? item.title : item.name]}}</div>
    <div>{{'Titolo in lingua originale:'+' '+[item.original_title ? item.original_title : item.original_name]}}</div> 
    <div>Lingua: <flag :iso="language"/></div>   
    <div>
        <span v-for="(n,index) in 5" :key="index">
            <i :class="n <= transformScale ? 'fa-solid fa-star golden-star' : 'fa-solid fa-star empty-star' "></i>
        </span>
    </div>   -->
    </div>
</template>

<script>
export default {
    name:'MainCard',
    props:{
        item:Object,
    },
    data(){
        return{
            image:'https://image.tmdb.org/t/p/w342',
        }
    },
    computed:{
        language(){
            if(this.item.original_language === 'en'){
                return 'gb'
            }else if(this.item.original_language === 'ja'){
                return 'jp'
            }else{
                return this.item.original_language
            }
        },
        imageFunc(){
            if(this.item.poster_path === null){
                return '/wwemzKWzjKYJFfCeiB57q3r4Bcm.png'
            }else{
                return this.item.poster_path 
            }
        },
        transformScale(){
           return parseInt(Math.ceil(this.item.vote_average / 2))
        },
    },
}
</script>

<style>
.poster-container{
    min-width: 180px;
    height: 260px;
    padding: 5px;
}
/* .golden-star{
    color: #D6B64C;
}
.empty-star{
    color:#D1D1D1;
}
.flag-icon-squared{
    background-color: black;
} */
</style>