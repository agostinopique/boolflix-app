<template>
    <div class="movie-container">
        <h1 class="text-light">{{titleCard}}</h1>
        <div v-if="MovieArr.length > 0" class="card-container">

            <CardComp
                v-for="movie in MovieArr"
                :key="movie.id"
                :Movie="movie"
            />
    
        </div>
        <h2 v-else class="text-light">Nessun Risultato</h2>
    </div>
</template>

<script>
import CardComp from './CardComp.vue';

export default {
    name: 'MovieComp',
    components:{
        CardComp
    },
    props: {
        MovieArr: Array,
        titleCard: String
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/mixins';

.movie-container h1{
    padding-top: 30px;
    padding-left: 10px;
}
.card-container{
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
</style>