<template>
<div class="poster-container align-items-center">
    <img class="img-fluid h-100 w-100" :src="image + imageFunc" alt="">
    <div class="description-container">
        <div>Titolo: <span>{{item.title ? item.title : item.name}}</span></div>
        <div>Titolo in lingua originale: <span>{{item.original_title ? titleFunc : titleFunc}}</span></div> 
        <div>Lingua: <flag :iso="language"/></div> 
        <div>Overview: <span>{{overviewFunc}}</span></div>  
        <div>
            <span v-for="(n,index) in 5" :key="index">
                <i :class="n <= transformScale ? 'fa-solid fa-star golden-star' : 'fa-solid fa-star empty-star' "></i>
            </span>
        </div> 
    </div>
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
        overviewFunc(){
            if(this.item.overview === ''){
                return 'Descrizione non disponibile'
            } else{
                return this.item.overview
            }
        },
        titleFunc(){
            if(this.item.original_title === this.item.title || this.item.original_name === this.item_name){
                return 'null'
            } else {
                return this.item.original_title || this.item.original_name
            }
        }
    },
}
</script>

<style lang="scss" scoped>
.poster-container{
    min-width: 180px;
    height: 260px;
    padding: 2px;
    position: relative;
    overflow-y: auto;
    .description-container{
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        display: none;
        padding: 10px;
        background-color: #9a9a9adf;
        overflow: auto;
    }
    &:hover .description-container{
        display: block;
    }
    
}
div{
    display: block;
    color: white;
    font-weight: 500;
    font-family: 'Roboto', sans-serif;
    font-size: 0.9em;
}
span{
    font-weight: 400;
    color:#000000 ;
}
 .golden-star{
    color: #D6B64C;
}
.empty-star{
    color:#D1D1D1;
}
.flag-icon-squared{
    background-color: black;
} 
</style>