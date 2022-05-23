<template>
    <div class="card-container"
        v-show="ResultsFound"
    >
        <MovieComp 
            :MovieArr = 'MovieArr'
        />
        <SeriesComp 
            :TvArr = 'TvArr'
        />
    </div>
</template>

<script>
import MovieComp from './MovieComp.vue';
import SeriesComp from './SeriesComp.vue';

export default {
    name: 'MainComp',
    components: {
        MovieComp,
        SeriesComp
    },
    props: {
        ResultsFound: Boolean,
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