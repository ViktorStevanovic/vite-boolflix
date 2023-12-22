<template lang="">
    <section class="results-list d-flex container text-center">
        <div class="movies-wrapper">
            <h1 class='mb-5'>Films</h1>            
            <SingleMovie v-for='movie in this.store.moviesList' :movie='movie'/>
        </div>

        <div class="series-wrapper">
            <h1 class='mb-5'>TV series</h1>
            <SingleSerie v-for='serie in this.store.seriesList' :serie='serie'/>
        </div>
    </section>
    
    
</template>
<script>
import { store } from '../js/store.js';
import SingleMovie from './SingleMovie.vue';
import SingleSerie from './SingleSerie.vue';
// import CountryFlag from '../../node_modules/vue-country-flag-next'
// import LangFlag from '../../node_modules/vue-lang-code-flags';


export default {
    name: 'AppMovies',
    data() {
        return {
            store,
            
        }
    },
    components: {
        SingleMovie,
        SingleSerie
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