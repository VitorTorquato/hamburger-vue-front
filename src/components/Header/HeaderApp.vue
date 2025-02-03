<template>
    <div>
        <header>
            <router-link to="/">
                <img id="logo" :src="logo" :alt="alt">
            </router-link>

            <nav id="nav">
                <router-link to="/">HOME</router-link>
                <router-link to="/order">ORDER</router-link>
            </nav>
        </header>

    </div>

</template>

<script>

    export default{
        name: 'HeaderApp',
        props:['logo' , 'alt']
    }
</script>

<style scoped>
    div{
        width: 100%;
        background-color: #222;
        border-bottom:4px solid #111;
    }

    header{
      

        width: 100%;
        max-width: 1400px;
        margin: 0 auto;
        height: 64px;
        padding: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    #logo{
        width: 48px;
        height: 48px;
    }

    #nav{
        display: flex;
        align-items: center;
        gap:10px;
    }

    #nav a{
        text-decoration: none;
        color: #FCBA03;
        font-size: 16px;
        transition: all .5s;
    }

    #nav a:hover{
        color: #FFF;

    }
</style>