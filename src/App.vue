<template>
  <div>
    <HeaderComp 
      @movieSearch="queryValue"
      @searchDefault="searchDefault"
    />

    <MainComp
      v-if="isLoaded"
      :MovieArr = 'movieArr'
      :TvArr = 'tvArr'
    />
    <div v-else class="loading text-light">
        <img src="./assets/img/agoflix.png" alt="">
        <div class="lds-ring"><div></div><div></div><div></div><div></div></div>
    </div>
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
      isLoaded: false
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
          this.isLoaded = true;

        } else { 

          this.tvArr = res.data.results
          this.isLoaded = true;

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
      this.isLoaded = false;
      this.apiParams.query = movie;
      console.log('ARRIVATO', this.apiParams.query);
      this.getApi(this.apiUrl,'movie');
      this.getApi(this.apiUrl,'tv');
    },
    
    searchDefault(){
      this.isLoaded = false;
      this.getApi(this.trendingUrl, 'movie/week')
      this.getApi(this.trendingUrl, 'tv/week')
    }
  }
}
</script>

<style lang="scss">
  @import './assets/style/general';

.loading{
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  img{
    width: 20%;
  }
}

.lds-ring {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-ring div {
  box-sizing: border-box;
  display: block;
  position: absolute;
  width: 64px;
  height: 64px;
  margin: 8px;
  border: 8px solid #fff;
  border-radius: 50%;
  animation: lds-ring 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  border-color: #DC1B28 transparent transparent transparent;
}
.lds-ring div:nth-child(1) {
  animation-delay: -0.45s;
}
.lds-ring div:nth-child(2) {
  animation-delay: -0.3s;
}
.lds-ring div:nth-child(3) {
  animation-delay: -0.15s;
}
@keyframes lds-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

</style>