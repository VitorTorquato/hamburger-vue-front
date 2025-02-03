<template>
    <div id="banner">
        <div class="hero-text">
            <h1>Make Your Burguer</h1>
        </div>
    </div>
</template>


<script>
    export default{
        name:'Banner',
    }
</script>

<style scoped>
    #banner{
        background-image: url('/img/burger.jpg');
        background-position: center center;
        background-size: cover;
        background-repeat: no-repeat;
        height: 100dvh;
        width: 100%;

        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    .hero-text{
        width: 100%;
        max-width: 1400px;
        margin: 0 auto;
    }
    .hero-text h1{

        color: #FFF;
        text-align: left;
        font-size: 48px;
        padding: 20px 40px 20px 10px; 
    }

</style>