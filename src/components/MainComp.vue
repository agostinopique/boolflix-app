<template>
    <div class="card-container">
        <MovieComp titleCard="Film"
            :MovieArr = 'MovieArr'
        />
        <MovieComp titleCard="Serie"
            :MovieArr = 'TvArr'
        />
    </div>
</template>

<script>
import MovieComp from './MovieComp.vue';
// import SeriesComp from './SeriesComp.vue';

export default {
    name: 'MainComp',
    components: {
        MovieComp,
        // SeriesComp
    },
    props: {
        MovieArr: Array,
        TvArr: Array
    }
}
</script>

<style lang="scss" scoped>
.card-container{
    padding-top: 30px;
    width: 80%;
    margin: 0 auto;
}
</style>