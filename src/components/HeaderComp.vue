<template>
    <header>
        <div class="head-img">
            <img src="../assets/img/Netflix-Logo.jpg" alt="">
        </div>
        <div class="input-area">
            <input type="text" class="form-control input" placeholder="Oggi ho voglia di...">
            
            <button class="btn btn-light input-btn">Cerca</button>
            
            <select name="genre" id="movie-genre">
                <option value="" selected>Select Genre</option>
                <option value="">MOVIES OR TV</option>
                <option value="">MOVIES OR TV</option>
                <option value="">MOVIES OR TV</option>
                <option value="">MOVIES OR TV</option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    name: 'HeaderComp'
}
</script>

<style lang="scss" scoped>
header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 15px;
    height: 100px;
    width: 100%;
    background-color: black;
    .head-img{
        width: 200px;
        height: 100%;
        img{
            width: 100%;
        }
    }
    .input-area{
        width: 50%;
        display: flex; 
        align-items: center;

        #movie-genre{
            margin-left: 10px;
            padding: 7px 10px;
        }
        .input-btn{
            margin: 0 5px;
        }
    }
}
</style>