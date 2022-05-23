<template>
    <div class="movie-container">
        <h1 class="text-light">Film</h1>
        <div class="card-container">

            <CardComp 
                v-for="movie in MovieArr"
                :key="movie.id"
                :Title="movie.title"
                :OrgTitle="movie.original_title"
                :OrgLang="movie.original_language"
                :Vote="movie.vote_average"
                :Overview="movie.overview"
            />

        </div>
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
        MovieArr: Array
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/mixins';

.movie-container h1{
    padding-left: 10px;
}
.card-container{
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
}
</style>