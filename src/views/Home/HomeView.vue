<script >
  import Banner from '@/components/Banner/Banner.vue';
  import BurguerForm from '@/components/Form/BurguerForm.vue';
  
  export default{
    components:{
      Banner,
      BurguerForm
    }
  }
</script>

<template>
  
    <Banner/>
  <main class="main_container">
    <h1 class="title">Make your burguer</h1>
    <BurguerForm />
  </main>
</template>

<style scoped>
    .main_container{
      width: 100%;
      max-width: 1400px;
      margin: 0 auto;
    }
    
    .title{
      margin-top: 36px;
    }
</style>
