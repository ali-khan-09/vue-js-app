<template>
<div class="container">
 <Header title="Task Tracker" @toggle-form="toggleform"  />
<div v-show="showAddTask">
   <Form @addTask="addTask"  />
</div>
 <Tasks :tasks="tasks"  @delete-task="deleteTask"  @toggle-reminder="toggleReminder" />
 
</div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue"
import Form from "./components/Form";

export default {
  name: 'App',
  components: {
   Header,
   Tasks,
   Form
  },
  data(){
    return {
      tasks:[],
      showAddTask:false,
    }
  },

  created()
  {

    this.tasks=[
      {
        id:1,
        text:"Doctor Apointment",
        time:"26 of Jan 8:08 PM",
        reminder:true,
      },
      {
        id:2,
        text:"Cricket Match",
        time:"29 of Feb 3:00 PM",
        reminder:true,
      },
      {
        id:3,
        text:"Watch The New Movie",
        time:"2 of March 4:00  PM",
        reminder:false,
      },
      {
        id:4,
        text:"Meeting With The One",
        time:"14 of Feb 9:00 PM",
        reminder:true,
      },
      
    ]
  },
  methods:{
    
    addTask(task)
    {
      this.tasks = [...this.tasks,task];

    },
    toggleform()
    {
       this.showAddTask = !this.showAddTask;
    }


    ,
    deleteTask(id)
    {
      this.tasks = this.tasks.filter((task)=> task.id !== id);
      console.log(id)
    },
    toggleReminder(id)
    {
      console.log(id)
      this.tasks= this.tasks.map((task)=> task.id == id ? {...task,reminder:!task.reminder}: task );
     
    }
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
