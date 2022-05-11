<template>
    <div>
        <div>{{'Titolo:'+' '+[item.title ? item.title : item.name]}}</div>
        <div>{{'Titolo in lingua originale:'+' '+[item.original_title ? item.original_title : item.original_name]}}</div> 
        <div>Lingua: <flag :iso="language(item)"/></div>   
        <div>
            <span v-for="(star,index) in tranfsormScale(item)" :key="index"><i class="fa-solid fa-star golden-star"></i></span>
            <span v-for="(star,index) in 5 - tranfsormScale(item)" :key="index"><i class="fa-solid fa-star empty-star"></i></span>
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
    methods:{
        language(film){
            if(film.original_language === 'en'){
                return film.original_language = 'gb'
            }else if(film.original_language === 'ja'){
                return film.original_language = 'jp'
            }else{
                return film.original_language
            }
        },
        tranfsormScale(film){
          return parseInt(film.vote_average / 2)
        },
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
</style>