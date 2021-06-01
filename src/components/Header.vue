<template>
    <header>
        <h1>{{text}}</h1>
        <Button 
          text="Add Task"
          @btn-click ="$emit('toggle-add-task')"
        />
    </header>
</template>


<script>
  import Button from './Button';

  export default {
    name: "Header",
    props:{
      text: String
    },
    components:{
      Button
    },
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