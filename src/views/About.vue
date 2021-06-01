<template>
  <div class="version">
    <p>Version 1.0.0</p>
    <router-link to="/">Go Back</router-link>
  </div>
</template>


<script>
  export default{
    name: "About"
  }
</script>


<style scoped>
  .version{
    text-align: center;
    padding: 40px;
  }
  .version p{
    font-size: 18px;
  }
</style>