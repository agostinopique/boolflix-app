<template>
    <div class="series-container">
        <h1 class="text-light">Series TV</h1>
        <div class="card-container">
            
            <CardComp />
            <CardComp />
            <CardComp />

        </div>
    </div>
</template>

<script>
import CardComp from './CardComp.vue';

export default {
    name: 'SeriesComp',
    components:{
        CardComp
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