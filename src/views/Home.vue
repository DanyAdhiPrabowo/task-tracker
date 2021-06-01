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
      async deleteTask(id){
        if(confirm("Are you sure?")){
          const deleteTask = await fetch(`api/tasks/${id}`, { method: "DELETE" });
          
          if(deleteTask.status === 200){
            this.tasks = this.tasks.filter((task)=> task.id !== id)
          }else{
            alert("Failed delete task!")
          }
        }
      },
      async toggleReminder(id){
        const getOneTask = await this.fetchTask(id);
        const dataUpdate = {...getOneTask, reminder: !getOneTask.reminder};

        const res = await fetch(`api/tasks/${id}`, {
          method: "PUT",
          headers:{ "Content-type": "application/json"},
          body: JSON.stringify(dataUpdate)
        });

        if(res.status === 200){
          this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder : !task.reminder} : task)
        }else{
          alert('Failed update reminder!')
        }
      },
      async addTask(task){
        const res = await fetch("api/tasks", {
          method: "POST",
          headers: { "Content-type": "application/json" },
          body: JSON.stringify(task)
        });

        if(res.status === 201){
          this.tasks = [...this.tasks, task]
        }else{
          alert("Failed add new task!")
        }
      },
      async fetchTasks(){
        const res = await fetch('api/tasks');
        const data = await res.json();
        return data
      },
      async fetchTask(id){
        const res = await fetch(`api/tasks/${id}`);
        const data = await res.json();
        return data
      }
    },

    async created(){
      this.tasks = await this.fetchTasks();
    },
  }
</script>