<template>
  <AddTask 
      @add-task = "addTask"
      v-show="showAddTask"
    />
    <Tasks 
      :tasks = "tasks" 
      @delete-task = "deleteTask"
      @toggle-reminder = "toggleReminder"
    />
</template>



<script>
  import AddTask from '../components/AddTask';
  import Tasks from '../components/Tasks';

  export default{
    name: "Home",
    components:{
      AddTask,
      Tasks
    },
    emits: ['showAddTask'],
    data(){
      return {
        tasks: []
      }
    },
    props:{
      showAddTask: Boolean
    },
    methods:{
      deleteTask(id){
        if(confirm("Are you sure?")){
          this.tasks = this.tasks.filter((task)=> task.id !== id)
        }
      },
      toggleReminder(id){
        this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder : !task.reminder} : task)
      },
      addTask(task){
        console.log(task)
        this.tasks = [...this.tasks, task]
      }
    },

    created(){
      this.tasks = [
        {
        "id": 1,
        "text": "Doctors",
        "day": "March 1st at 2:30pm",
        "reminder": true
        },
        {
          "id": 2,
          "text": "Meeting at School",
          "day": "March 3st at 1:30pm",
          "reminder": true
        },
        {
          "id": 3,
          "text": "Food shopping",
          "day": "March 3st at 2:30pm",
          "reminder": false
        },
      ];
    },
  }
</script>