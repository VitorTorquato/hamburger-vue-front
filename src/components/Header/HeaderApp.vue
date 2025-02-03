<template>
    <div>
        <header>
            <router-link to="/">
                <img id="logo" src="">
            </router-link>

            <nav id="nav">
                <router-link to="/">Home</router-link>
                <router-link to="/order">Order</router-link>
            </nav>
        </header>

    </div>

</template>

<script>

    export default{
        name: 'HeaderApp'
    }
</script>

<style scoped>
    div{
        width: 100%;
        
    }

    header{
        width: 100%;
        max-width: 1224px;
        margin: 0 auto;
        height: 64px;
        padding: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    #nav{
        display: flex;
        align-items: center;
        gap:10px
    }
</style>