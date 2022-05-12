<template>
    <div>
        <div>{{'Titolo:'+' '+[item.title ? item.title : item.name]}}</div>
        <div>{{'Titolo in lingua originale:'+' '+[item.original_title ? item.original_title : item.original_name]}}</div> 
        <div>Lingua: <flag :iso="language"/></div>   
        <div>
            <span v-for="(n,index) in 5" :key="index">
                <i :class="n <= transformScale ? 'fa-solid fa-star golden-star' : 'fa-solid fa-star empty-star' "></i>
            </span>
        </div>  
        <img class="img-fluid" :src="image + item.poster_path" alt="">
    </div>
</template>

<script>
export default {
    name:'AppGrid',
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
        transformScale(){
           return parseInt(Math.ceil(this.item.vote_average / 2))
        },
    },
    methods:{
        
    }
     
}
</script>

<style lang="scss">
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