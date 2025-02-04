<script>
  import Dashboard from '@/components/Dashboard/Dashboard.vue';
  export default{
    components:{
      Dashboard
    },
    name:'Orders'
  }
</script>

<template>
  <div class="main_container">
    <h1>Orders</h1>
    <Dashboard />
  </div>
</template>

<style scoped>
  .main_container{
    width: 100%;
    max-width: 1400px;
    min-height: calc(100dvh - 139px);
    margin: 0 auto;
  }

  h1{
    margin-top: 36px;
  }
</style>