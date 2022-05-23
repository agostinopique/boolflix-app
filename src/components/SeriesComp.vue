<template>
    <div class="series-container">
        <h1 class="text-light">Series TV</h1>
        <div class="card-container">
            
            <CardComp 
                v-for="serie in TvArr"
                :key="serie.id"
                :Title="serie.name"
                :OrgTitle="serie.original_name"
                :OrgLang="serie.original_language"
                :Vote="serie.vote_average"
                :Overview="serie.overview"
                :Poster="serie.poster_path"

            />

        </div>
    </div>
</template>

<script>
import CardComp from './CardComp.vue';

export default {
    name: 'SeriesComp',
    components:{
        CardComp
    },
    props:{
        TvArr: Array
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/mixins';
.series-container h1{
    padding-top: 30px;
    padding-left: 10px;
}
.card-container{
    @include contentCenter;
    flex-wrap: wrap;
}
</style>