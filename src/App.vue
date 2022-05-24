<template>
  <div>
    <HeaderComp 
      @movieSearch="queryValue"
      @searchDefault="searchDefault"
    />

    <MainComp 
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
      trendingUrl: ' https://api.themoviedb.org/3/trending/',
      
      apiParams:{
        api_key: 'bd3bc2b6fb03fa83d69033826264bb1d',
        query: '',
        language: 'it-IT'
      },

      movieArr: [],
      tvArr:[],
    }
  },

  mounted(){
    this.getApi(this.trendingUrl, 'movie/week')
    this.getApi(this.trendingUrl, 'tv/week')
  },

  methods: {
    getApi(url, type){
      axios.get(url + type, {
        params: this.apiParams
      })

      .then((res) => {
        console.log(res);

        if(type === 'movie' || type === 'movie/week'){

          this.movieArr = res.data.results;

        } else { 

          this.tvArr = res.data.results

        }

        this.apiParams.query = ''; 

        console.log('MOVIES',this.movieArr);
        console.log('TVSERIES' ,this.tvArr);
      })

      .catch((error) => {
        console.log('ERRORE', error)
      })
    },

    queryValue(movie){
      // this.movieArr = [];
      // this.tvArr = []; 

      this.apiParams.query = movie;
      console.log('ARRIVATO', this.apiParams.query);
      this.getApi(this.apiUrl,'movie');
      this.getApi(this.apiUrl,'tv');
    },
    
    searchDefault(){
      this.getApi(this.trendingUrl, 'movie/week')
      this.getApi(this.trendingUrl, 'tv/week')
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';

</style>