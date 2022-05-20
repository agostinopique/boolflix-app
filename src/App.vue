<template>
  <div>
    <HeaderComp 
      @movieSearch="queryValue"
    />

    <MainComp 
      :ResultsFound = 'resultsFound'
      :MovieArr = 'movieArr'
    />

  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import MainComp from './components/MainComp.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    HeaderComp,
    MainComp
  },

  data(){
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/movie/?',
      
      apiParams:{
        api_key: 'bd3bc2b6fb03fa83d69033826264bb1d',
        query: '',
        language: 'it-IT'
      },

      movieArr: [],
      resultsFound: false
    }
  },

  methods: {
    getApi(){
      console.log(this.apiParams)
      axios.get(this.apiUrl, {
        params: this.apiParams
      })
      .then((res) => {
        this.movieArr = res.data.results;
        this.resultsFound = true; 
        console.log(this.movieArr);
      })
      .catch((error) => {
        console.log('ERRORE', error)
      })
    },

    queryValue(movie){
      this.apiParams.query = movie;
      console.log('ARRIVATO', this.apiParams.query);
      this.getApi();
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';

</style>
