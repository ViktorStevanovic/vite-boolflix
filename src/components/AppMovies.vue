<template lang="">
    <section class="results-list d-flex container text-center">
        <div class="movies-wrapper">
            <h1 class='mb-5'>Films</h1>
            <article v-for='movie in this.store.moviesList' class='d-flex flex-column justify-content-center align-items-center gap-3'>
                <h1>{{ movie.title}}</h1>
                <p>Original title: {{movie.original_title}}</p>
                <!-- <img :src="`https://image.tmdb.org/t/p/w500${movie.poster_path}`" alt=""> -->
                <img :src="(movie.poster_path != null) ? `http://image.tmdb.org/t/p/w500/${movie.poster_path}` : 'https://static.vecteezy.com/system/resources/previews/005/337/799/original/icon-image-not-found-free-vector.jpg' " alt="">

                <!-- <country-flag :country='movie.original_language'/> -->
                <lang-flag :iso='movie.original_language'/>
                <p>{{roundUp(movie.vote_average)}}</p>      
            </article>
        </div>
        <div class="series-wrapper">
            <h1 class='mb-5'>TV series</h1>
            <article v-for='serie in this.store.seriesList' class='d-flex flex-column justify-content-center align-items-center gap-3'>
                <h1>{{ serie.name}}</h1>
                <p>Original title: {{serie.original_name}}</p>
                <img :src="`https://image.tmdb.org/t/p/w500${serie.poster_path}`" alt="">

                <!-- <country-flag :country='movie.original_language'/> -->
                <lang-flag :iso='serie.original_language'/>
                <p>{{roundUp(serie.vote_average)}}</p>      
            </article>
        </div>
    </section>
    
    
</template>
<script>
import { store } from '../js/store.js';
// import CountryFlag from '../../node_modules/vue-country-flag-next'
import LangFlag from '../../node_modules/vue-lang-code-flags';


export default {
    name: 'AppMovies',
    data() {
        return {
            store,
            
        }
    },
    components: {
        LangFlag
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
   .movies-wrapper,.series-wrapper{
    width: 50%;
   }
   img{
    width: 500px;
   }
 
</style>