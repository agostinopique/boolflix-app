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
                    <lang-flag v-if="flags.default.includes(Movie.original_language)" :iso="Movie.original_language" :squared="false" />
                    <p v-else> Lingua: {{Movie.original_language}}</p> 
                    <div v-if="Movie.vote_average != 0">
                        <p>Voto: {{(Movie.vote_average / 2).toFixed(1)}}</p>
                        <!-- PER LE STELLE SI POTEVA AGGIUNGERE LE CLASSI ALLE ICONE DELLE STELLE DI BOOTSTRAP (LA CASSE FA-STAR È COMUNE A TUTTE, CAMBIA SOLO LA SECONDA CLASSE IN BASE A SE È PIENA O VUOTA) FACENDO CICLARE IL TAG DELLA STELLA CON UN V-FOR='I IN 5' AGGIUNGENDO POI UNA CLASSE DINAMICA :CLASS CON UNA CONDIZIONE PER IL QUALE SE I <= VOTO LA STELLA ERA PIENA : ALTRIMENTI È VUOTE -->
                        <p id="stars" v-html="starsCreation(Movie.vote_average / 2)"></p>
                    </div>
                        <p v-else>Voto non disponibile</p>
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
        LangFlag
    },

    data(){
        return{
            flags: require('../assets/script/flag.js')
        }
    },


    props:{
        Movie: Object
    },

    methods:{
        starsCreation(vote){
            let stars = '';
            let i = 0;
            let decimalNumber = 0;
            while(i < Math.round(vote)){
                decimalNumber = parseInt(vote.toString().charAt(2));
                console.log('Numero decimale', decimalNumber)
                stars += `<i class="fa-solid fa-star"></i>`;
                // stars += `<i class="bi bi-star-fill"></i>`;
                i++;
                if(decimalNumber >= 5 && i === Math.round(vote - 1)){
                    stars += `<i class="fa-regular fa-star-half-stroke fa-star"></i>`;
                    // stars += `<i class="bi bi-star-half"></i>`;
                    i++;
                }
            }

            let empty = 0;
            let a = 0;
            if(decimalNumber >= 5){
                empty = 5 - Math.ceil(vote)
            } else {
                empty = 5 - Math.floor(vote)
            }
            while(a < empty){
                stars += `<i class="fa-regular fa-star"></i>`;
                // stars += `<i class="bi bi-star"></i>`;
                a++;
            }
            console.log(typeof stars)


            return stars
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
    box-shadow: 0 0px 12px 0 rgba(255, 255, 255, 0.2);
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