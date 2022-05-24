<template>
    <header>
        <div class="head-img" @click="$emit('searchDefault')">
            <img src="../assets/img/agoflix.png" alt="">
        </div>
        <div class="input-area">
            <input
                v-model.trim="query"
                @keyup.enter="movieSearch"
                type="text" 
                class="form-control input" 
                placeholder="Oggi ho voglia di...">

            <button class="btn btn-light input-btn"
                @click="movieSearch"
            >Cerca</button>

        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderComp',
    data(){
        return{
            query: ''
        }
    },
    methods: {
        movieSearch(){
            console.log( this.query )
            if(this.query != ''){
                this.$emit('movieSearch', this.query);
            }
            this.query = ''
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/mixins';

header{
    @include alignCenter();
    justify-content: space-between;
    padding: 0 15px;
    height: 100px;
    width: 100%;
    background-color: black;
    .input-area{
        @include alignCenter();
        width: 50%;

        #movie-genre{
            margin-left: 10px;
            padding: 7px 10px;
        }
        .input-btn{
            margin: 0 5px;
        }
    }
    .head-img{
        cursor: pointer;
    }
}
</style>