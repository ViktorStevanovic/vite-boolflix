<template lang="">
    <!-- <h1>{{this.store.moviesList[0].title}}</h1> -->
    <div v-for='movie in this.store.moviesList'>
        <h1>Title: {{ movie.title}}</h1>
        <p>Original title: {{movie.original_title}}</p>
        <p>Language: {{movie.original_language}}</p>
        <p>Feedback: {{movie.vote_average}}</p>
    </div>
</template>
<script>
import { store } from '../js/store.js';
export default {
    name: 'AppMovies',
    data() {
        return {
            store
        }
    },
}
</script>
<style lang="scss" scoped>
    
</style>