<template>
    <div>
        <span>{{'Titolo:'+' '+[item.title ? item.title : item.name]}}</span>
        <span>{{'Titolo in lingua originale:'+' '+[item.original_title ? item.original_title : item.original_name]}}</span> 
        <span>Lingue: <flag :iso="language(item)"/></span>   
        <span>{{'Voto:'+' '+item.vote_average}}</span> 
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
        }
    }
     
}
</script>

<style lang="scss">
span{
    display: block;
}
</style>