<template>
    <header>
        <h1>{{text}}</h1>
        <Button 
          v-show="homePage"
          :text="showAddTask ? 'Close' : 'Add Task'"
          :color="showAddTask ? 'red' : 'green'"
          @btn-click ="$emit('toggle-add-task')"
        />
    </header>
</template>


<script>
  import Button from './Button';

  export default {
    name: "Header",
    props:{
      "text": String,
      "showAddTask": Boolean
    },
    components:{
      Button
    },
    computed:{
      homePage(){
        if(this.$route.path === '/'){
          return true
        }else{
          return false
        }
      }
    }

  }
</script>


<style scoped>
  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>