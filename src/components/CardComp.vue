<template>
    <div class="card-element">
        <div class="card-content">
            <div class="card-front">
                <img v-if="Movie.poster_path != null" :src="`https://image.tmdb.org/t/p/w342/${Movie.poster_path}`" :alt="Movie.title || Movie.name">
                <span v-else>
                    <img src="../assets/img/poster_placeholder.jpg" :alt="Movie.title || Movie.name">
                    <h4 class="alternative-title">{{Movie.title || Movie.name}}</h4>
                </span>
            </div>
            <div class="card-back">
                <div class="main-info">
                    <h4>{{Movie.title || Movie.name}}</h4> 
                    <p>{{Movie.original_title || Movie.original_name}}</p>
                    <lang-flag :iso="Movie.original_language" :squared="false" />
                    <!--  <p v-else>{{Movie.original_language || Movie.original_language}}</p>  -->
                    <p id="stars">{{averageVote(Movie.vote_average)}}</p>
                </div>
                <p class="overview-movie">{{Movie.overview}}</p>
            </div>
        </div>
    </div>
</template>

<script>
import LangFlag from '../../node_modules/vue-lang-code-flags';

export default {
    name: 'CardComp',
    components:{
        LangFlag,
    },


    props:{
        Movie: Object
    },

    methods:{
        averageVote(vote){
            let average = vote / 2;

            /* for(let i = 0; i >= average; i++){
                document.getElementById('stars').innerText += 'Suck'
            } */
            return  average = Math.round(average);
        }

    }
}
</script>

<style lang="scss" scoped>
.alternative-title{
    width: 100%;
    text-align: center;
    position: relative;
    bottom: 150px;

}

.card-element {
    background-color: transparent;
    min-width: 300px;
    height: 400px;
    perspective: 1000px;
    margin: 15px;
}

.card-content {
    position: relative;
    width: 100%;
    height: 100%;
    transition: transform 0.6s;
    transform-style: preserve-3d;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.card-element:hover .card-content {
    transform: rotateY(180deg);
}

.card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
}

.card-front {
    background: rgb(2,0,36);
    color: black;
    width: 100%;
    height: 100%;
    img{
        width: 100%;
        height: 100%;
        line-height: 400px;
        text-align: center;
        object-fit: cover;
    }
}

.card-back {
    background-color: #332f2f8b;
    color: white;
    transform: rotateY(180deg);
    padding: 5px 0 5px 5px;
    .main-info{
        max-height: 50%;
        padding: 5px;
        margin-bottom: 10px;
    }
}

.overview-movie{
    max-height: 50%;
    overflow-y: auto;
}
</style>