<template lang="">
    <section class="results-list d-flex">
        <div class="movies-wrapper">
            <h1>Films</h1>
            <article v-for='movie in this.store.moviesList'>
                <h1>Title: {{ movie.title}}</h1>
                <p>Original title: {{movie.original_title}}</p>
                <!-- <country-flag :country='movie.original_language'/> -->
                <lang-flag :iso='movie.original_language'/>
                <p>Feedback: {{movie.vote_average}}</p>      
            </article>
        </div>
        <div class="series-wrapper">
            <h1>TV series</h1>
            <article v-for='serie in this.store.seriesList'>
                <h1>Title: {{ serie.name}}</h1>
                <p>Original title: {{serie.original_name}}</p>
                <!-- <country-flag :country='movie.original_language'/> -->
                <lang-flag :iso='serie.original_language'/>
                <p>Feedback: {{serie.vote_average}}</p>      
            </article>
        </div>
    </section>
    
    
</template>
<script>
import { store } from '../js/store.js';
// import CountryFlag from '../../node_modules/vue-country-flag-next'
import LangFlag from '../../node_modules/vue-lang-code-flags'

export default {
    name: 'AppMovies',
    data() {
        return {
            store,
            
        }
    },
    components: {
                LangFlag
            }
}
</script>
<style lang="scss" scoped>
   
</style>