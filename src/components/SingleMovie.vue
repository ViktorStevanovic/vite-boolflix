<template>
    <article class='d-flex justify-content-center align-items-center gap-3'>
        <div class="cover-image">
            <img :src="(movie.poster_path != null) ? `http://image.tmdb.org/t/p/w342/${movie.poster_path}` : 'https://static.vecteezy.com/system/resources/previews/005/337/799/original/icon-image-not-found-free-vector.jpg' " alt="">
        </div>
        <div class="movie-info flex-column justify-content-end align-items-center gap-2">
            <h1 class="text-wrap">{{ movie.title}}</h1>
            <p class="text-wrap"><strong>Original title:</strong> {{movie.original_title}}</p>    
            <lang-flag :iso='movie.original_language'/>
            <p>{{roundUp(movie.vote_average)}}</p>      
        </div>
    </article>
</template>
<script>
import { store } from '../js/store.js';
import LangFlag from '../../node_modules/vue-lang-code-flags';

export default {
    name: 'SingleMovie',
    components:{
        LangFlag
    },
    props:{
        movie:{
            type: Object,
            required: true,
            
        }
    },
    data() {
        return {
            store
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
    article{
        height: 100%;
        width: 320px;
        position: relative;
        &:hover{
            .movie-info{
                display: flex;
                background-color: rgba(0, 0, 0, 0.7);
            }
        }

        .cover-image{
            height: 100%;
            width: 100%;
            z-index: 0;
            img{
                height: 100%;
                width: 320px;
                position: relative;
                object-fit: cover;
                object-position: center;
            }
        }
        .movie-info{
            height: 100%;
            width: 100%;
            position: absolute;
            bottom: 0;
            color: white;
            z-index: 1;
            display: none;
            h1{
                font-size: 1rem;
            }

        }
    }
</style>