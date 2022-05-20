<template>
    <div class="card-container">
        <div class="card-element text-light">
            <h2>titolo</h2>
            <h2>titolo originale</h2>
            <h2>voto</h2>
            <h2>trama</h2>
        </div>
        <div class="card-element text-light">
            <h2>titolo</h2>
            <h2>titolo originale</h2>
            <h2>voto</h2>
            <h2>trama</h2>
        </div>
        <div class="card-element text-light">
            <h2>titolo</h2>
            <h2>titolo originale</h2>
            <h2>voto</h2>
            <h2>trama</h2>
        </div>
        <div class="card-element text-light">
            <h2>titolo</h2>
            <h2>titolo originale</h2>
            <h2>voto</h2>
            <h2>trama</h2>
        </div>
        <div class="card-element text-light">
            <h2>titolo</h2>
            <h2>titolo originale</h2>
            <h2>voto</h2>
            <h2>trama</h2>
        </div>
        <div class="card-element text-light">
            <h2>titolo</h2>
            <h2>titolo originale</h2>
            <h2>voto</h2>
            <h2>trama</h2>
        </div>
       
    </div>
</template>

<script>
export default {
    name: 'MainComp'
}
</script>

<style lang="scss" scoped>
.card-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;

    .card-element{
        min-width: 300px;
        height: 600px;
        border: 1px solid white;
    }
}
</style>