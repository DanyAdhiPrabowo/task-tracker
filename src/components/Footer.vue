<template>
  <footer>
    <p>Copyright &copy; 2021</p>
    <router-link to="/about" v-show="aboutPage">About</router-link>
  </footer>
</template>

<script>
  export default{
    name: "Footer",
    computed:{
      aboutPage(){
        if(this.$route.path === "/about"){
          return false
        }else{
          return true
        }
      }
    }
  }
</script>


<style scoped>
  footer{
    margin-top: 30px;
    padding: 20px;
    background-color:#e3e6e5;
    text-align:center
  }
</style>