<template lang="">
    <section class="results-list container-fluid text-center">
        <!-- Movie section -->
        <div class="movies-wrapper d-flex gap-3 p-1">
            <!-- <h1 class='mb-5'>Films</h1>             -->
            <SingleMovie v-for='movie in this.store.moviesList' :movie='movie'/>
        </div>
        <!-- TV Series section -->
        <div class="series-wrapper d-flex gap-3 p-1">
            <!-- <h1 class='mb-5'>TV series</h1> -->
            <SingleSerie v-for='serie in this.store.seriesList' :serie='serie'/>
        </div>
    </section>
    
    
</template>
<script>
import { store } from '../js/store.js';
import SingleMovie from './SingleMovie.vue';
import SingleSerie from './SingleSerie.vue';

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
    overflow: scroll;
    white-space: nowrap;
    height: 50%;
    -ms-overflow-style: none;
    scrollbar-width: none;
   }
   .movies-wrapper::-webkit-scrollbar{
    display: none;
    
   }

   section{
    height: calc(100vh - 56px);
    background-color: #202529;
   }
 
</style>