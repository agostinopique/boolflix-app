<template>
    <!-- <div class="card-element text-light">
        <h2>titolo</h2>
        <h2>titolo originale</h2>
        <h2>voto</h2>
        <h2>trama</h2>
    </div> -->
    <div class="card-element">
        <div class="card-content">
            <div class="card-front">
                <!-- <img src="img_avatar.png" alt="Poster"> -->
            </div>
            <div class="card-back">
                <h1>{{MovieCard.title}}</h1> 
                <p>{{MovieCard.original_title}}</p> 
                <p>{{MovieCard.vote_average}}</p>
                <p class="overview-movie">{{MovieCard.overview}}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CardComp',
    props:{
        MovieCard: Object
    },

    methods:{

    }
}
</script>

<style lang="scss" scoped>

.card-element {
    background-color: transparent;
    min-width: 300px;
    height: 400px;
    perspective: 1000px;
    margin: 5px 5px;
}

.card-content {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
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
    background-color: #bbb;
    color: black;
}

.card-back {
    background-color: #332f2f;
    color: white;
    transform: rotateY(180deg);
    padding: 5px 0 5px 5px;
}

.overview-movie{
    height: 210px;
    overflow-y: auto;
}
</style>