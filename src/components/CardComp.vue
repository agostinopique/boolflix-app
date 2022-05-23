<template>
    <div class="card-element">
        <div class="card-content">
            <div class="card-front">
                <img :src="`https://image.tmdb.org/t/p/w342/${Poster}`" :alt="Title">
            </div>
            <div class="card-back">
                <div class="main-info">
                    <h3>{{Title}}</h3> 
                    <p>{{OrgTitle}}</p>
                    <lang-flag :iso="OrgLang" :squared="false" />
                    <!-- <p>{{MovieCard.original_language}}</p>  -->
                    <p id="stars">{{averageVote(Vote)}}</p>
                </div>
                <p class="overview-movie">{{Overview}}</p>
            </div>
        </div>
    </div>
</template>

<script>
import LangFlag from '../../node_modules/vue-lang-code-flags';


export default {
    name: 'CardComp',
    components:{
        LangFlag
    },


    props:{
        Title: String,
        OrgTitle: String,
        OrgLang: String,
        Vote: Number,
        Overview: String,
        Poster: String
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
    background: linear-gradient(124deg, rgba(2,0,36,1) 10%, rgba(219,40,5,1) 29%, rgba(224,41,5,1) 60%, rgba(15,15,15,1) 92%);
    color: black;
    width: 100%;
    img{
        width: 100%;
        height: 100%;
        line-height: 400px;
        text-align: center;
        object-fit: cover;
    }
}

.card-back {
    background-color: #332f2f;
    color: white;
    transform: rotateY(180deg);
    padding: 5px 0 5px 5px;
    .main-info{
        height: 50%;
        padding: 5px;
        margin-bottom: 10px;
    }
}

.overview-movie{
    height: 50%;
    overflow-y: auto;
}
</style>