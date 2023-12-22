<template>
    <article  class='d-flex flex-column justify-content-center align-items-center gap-3'>
        <h1>{{ serie.name}}</h1>
        <p>Original title: {{serie.original_name}}</p>
        <img :src="`https://image.tmdb.org/t/p/w500${serie.poster_path}`" alt="">
        <lang-flag :iso='serie.original_language'/>
        <p>{{roundUp(serie.vote_average)}}</p>      
    </article>
</template>
<script>
import { store } from '../js/store.js';
import LangFlag from '../../node_modules/vue-lang-code-flags';
export default {
    name: 'SingleSerie',
    components:{
        LangFlag
    },
    data() {
        return {
            store
        }
    },
    props:{
        serie:{
            type: Object,
            required: true,
            
        }
    },
    methods: {
        roundUp(vote){
            let raiting = '';
            for (let index = 0; index < this.store.moviesList.length; index++) {
                let result = parseInt(vote / 2);            
                result = Math.round(result);
                // console.log(result)
            for (let index = 0; index < result; index++) {
                raiting += "★"            
            } 
                return raiting             
            }
        }
    },
}
</script>
<style lang="scss" scoped>
    
</style>