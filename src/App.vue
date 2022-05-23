<template>
  <div>
    <HeaderComp 
      @movieSearch="queryValue"
    />

    <MainComp 
      :ResultsFound = 'resultsFound'
      :MovieArr = 'movieArr'
      :TvArr = 'tvArr'
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
      movieUrl: 'https://api.themoviedb.org/3/search/movie',
      tvUrl: 'https://api.themoviedb.org/3/search/tv',
      
      apiParams:{
        api_key: 'bd3bc2b6fb03fa83d69033826264bb1d',
        query: '',
        language: 'it-IT'
      },

      movieArr: [],
      tvArr:[],
      resultsFound: false
    }
  },

  mounted:{
    // getDefaultMovies()
  },

  methods: {
    getApi(apiUrl){
      axios.get(apiUrl, {
        params: this.apiParams
      })
      .then((res) => {
        console.log(res);
        if(this.movieArr.length < 1){
          this.movieArr = res.data.results;
        } else {
          this.tvArr = res.data.results
        }
        this.resultsFound = true;
        this.apiParams.query = '';
        console.log('MOVIES',this.movieArr);
        console.log('TVSERIES' ,this.tvArr);
      })
      .catch((error) => {
        console.log('ERRORE', error)
      })
    },

    queryValue(movie){
      this.apiParams.query = movie;
      console.log('ARRIVATO', this.apiParams.query);
      this.getApi(this.movieUrl);
      this.getApi(this.tvUrl);
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';

</style>
