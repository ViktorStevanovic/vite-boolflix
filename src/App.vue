<template>  
  <AppHeader/>
  <AppMain/>
</template>
<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './js/store.js';
import axios from 'axios';
export default {
  name: 'App',
  components:{
    AppHeader,
    AppMain
  },
  data() {
    return {
      store,
    }
  },
}
</script>
<style lang="scss">
    @use './styles/general.scss';
</style>