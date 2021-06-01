<template>
  <form class="add-form" @submit="onSubmit">
    <div class="form-control">
      <label>Task</label>
      <input  type="text" name="text" placeholder="Add Task" v-model="text">
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input type="date" name="day" v-model="day">
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" name="reminder" v-model="reminder">
    </div>

    <input class="btn btn-block" type="submit" value="Save">

  </form>
</template>



<script>
export default {
  name: 'AddTask',
  data(){
    return{
      text: '',
      day: '',
      reminder: false
    }
  },
  methods:{
    onSubmit(e){
      e.preventDefault()
      if(!this.text){
        alert('Task cannot be empty!')
        return
      }
      if(!this.day){
        alert('Day cannot be empty!')
        return
      }
      const newTask = {
        id: Math.floor(Math.random() * 1000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      };

      this.$emit('add-task', newTask);

      this.text = ''
      this.day = ''
      this.reminder = false


    }
  }
}
</script>



<style scoped>
  .add-form{
    margin-bottom: 40px;
  }

  .form-control{
    margin: 20px 0;
  }

  .form-control label{
    display: block;
  }

  .form-control input{
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
  }

  .form-control-check{
    display: flex;
    align-items: center;
    justify-content: space-between;
  } 

  .form-control-check label{
    flex: 1;
  }

  .form-control-check input{
    float: 2;
    height: 20px;
  }
</style>