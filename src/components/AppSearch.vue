<template lang="">
    <nav class="navbar bg-body-tertiary">
        <div class="container">
            <a class="navbar-brand">Boolflix</a>
            <form class="d-flex" role="search" v-on:submit.prevent>
            <input class="form-control me-2" type="text" placeholder="Search" aria-label="Search" v-model="movieName" v-on:keyup.enter='changeMovie'>
            <button class="btn btn-outline-danger" type="button" @click='changeMovie'>Search</button>
            </form>
        </div>
</nav>
</template>

<script>
import { store } from '../js/store.js';
import axios from 'axios';


export default {
    name: 'AppSearch',
    data() {
        return {
            store,
            movieName:'',
        }
    },
    methods: {
        changeMovie(){
        this.getMovie('https://api.themoviedb.org/3/search/movie?api_key=92d62557ab1a829ebff768d97ab5dc74&language=it_IT&query=' + this.movieName);
        this.getSeries('https://api.themoviedb.org/3/search/tv?api_key=92d62557ab1a829ebff768d97ab5dc74&language=it_IT&query=' + this.movieName)
      },

        getMovie(url = 'https://api.themoviedb.org/3/search/movie?api_key=92d62557ab1a829ebff768d97ab5dc74&language=it_IT&query='){
            axios.get(url)
            .then((response) => {
            // handle success
            console.log(response.data.results);
            this.store.moviesList = response.data.results;
            })
            .catch(function (error) {
            // handle error
            console.error(error);
            });
        },
        getSeries(url = 'https://api.themoviedb.org/3/search/tv?api_key=92d62557ab1a829ebff768d97ab5dc74&language=it_IT&query='){
            axios.get(url)
            .then((response) => {
            // handle success
            console.log(response.data.results);
            this.store.seriesList = response.data.results;
            })
            .catch(function (error) {
            // handle error
            console.error(error);
            });
        },
    },
}
</script>
<style lang="scss" scoped>
    
</style>