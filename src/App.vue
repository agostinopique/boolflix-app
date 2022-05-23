<!-- 
  RITOCCHI DA FARE:

  1. ALTERNATIVA DELLA LINGUA SE LA BANDIERINA È

  immagini: object fit
-->
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
      apiUrl: 'https://api.themoviedb.org/3/search/',
      trendingUrl: ' https://api.themoviedb.org/3/trending/movie/week?api_key=bd3bc2b6fb03fa83d69033826264bb1d',
      
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
    getApi(type){
      axios.get(this.apiUrl + type, {
        params: this.apiParams
      })

      .then((res) => {
        console.log(res);

        if(type === 'movie'){

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
      this.movieArr = [];
      this.tvArr = []; 

      this.apiParams.query = movie;
      console.log('ARRIVATO', this.apiParams.query);
      this.getApi('movie');
      this.getApi('tv');
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';

</style>