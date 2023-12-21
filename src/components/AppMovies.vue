<template lang="">
    <!-- <h1>{{this.store.moviesList[0].title}}</h1> -->
    <div v-for='movie in this.store.moviesList'>
        <h1>Title: {{ movie.title}}</h1>
        <p>Original title: {{movie.original_title}}</p>
        <!-- <country-flag :country='movie.original_language'/> -->
        <lang-flag :iso='movie.original_language'/>
        <p>Feedback: {{movie.vote_average}}</p>
        
    </div>
    
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