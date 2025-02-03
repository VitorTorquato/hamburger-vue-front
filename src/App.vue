<script >
  import HeaderApp from './components/Header/HeaderApp.vue';
  import FooterApp from './components/Footer/FooterApp.vue';

  export default{
    components:{
      HeaderApp,
      FooterApp
    },
    data(){
      return{
        logo_src: '/img/logo.png',
        app_name: 'Make your burguer'
      }
    }
  }


</script>

<template>
  <div>
    <HeaderApp :logo="logo_src" :alt="app_name"/>
    <routerView/>
    <FooterApp/>
  </div>
</template>

<style>
 *{
  font-family: 'Helvetica' , sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.main_container{
  margin: 50px;
  min-height: calc(100dvh - 250px);
}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>

