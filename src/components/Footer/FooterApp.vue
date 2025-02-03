<template>
    <div>
        <footer><p>Make Your Burger &copy; 2025</p></footer>
    </div>
</template>

<script>
    export default{
        name:'Footer'
    }

</script>

<style scoped>

    div{
        width: 100%;
        background-color: #222;
        border-top: 4px solid #111;
    }

    footer{
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        max-width: 1224px;
        padding: 24px 10px;
        margin: 0 auto;
        color: #FCBA03;
    }
</style>