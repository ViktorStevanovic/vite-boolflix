<template>
    <article class='d-flex justify-content-center align-items-center gap-3'>
        <div class="cover-image">
            <img :src="(movie.poster_path != null) ? `http://image.tmdb.org/t/p/w342/${movie.poster_path}` : 'https://static.vecteezy.com/system/resources/previews/005/337/799/original/icon-image-not-found-free-vector.jpg' " alt="">
        </div>
        <div class="movie-info">
            <h1>{{ movie.title}}</h1>
            <p>Original title: {{movie.original_title}}</p>    
            <lang-flag :iso='movie.original_language'/>
            <p>{{roundUp(movie.vote_average)}}</p>      
        </div>
    </article>
    <!-- <article class='d-flex justify-content-center align-items-center gap-3'>
        <h1>{{ movie.title}}</h1>
        <p>Original title: {{movie.original_title}}</p>
        <img :src="(movie.poster_path != null) ? `http://image.tmdb.org/t/p/w342/${movie.poster_path}` : 'https://static.vecteezy.com/system/resources/previews/005/337/799/original/icon-image-not-found-free-vector.jpg' " alt="">
        <lang-flag :iso='movie.original_language'/>
        <p>{{roundUp(movie.vote_average)}}</p>      
    </article> -->
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
        width: 350px;
        position: relative;
        &:hover{
            .movie-info{
                display: block;
                background-color: rgba(0, 0, 0, 0.512);
            }
        }

        .cover-image{
            height: 100%;
            width: 100%;
            z-index: 0;
            img{
                height: 100%;
                position: relative;
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