<template>
   <div class="container">
      <Header @toggle-add-task='toggleAddTask'  
      title="Task Tracker" 
      :showAddTask="showAddTask"/>
      <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
      </div>
      <!-- now we have access to task data -->
      <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
   </div>

</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  
  },
  // This is our State management area
  // where we get our data, data is a FUNCTION THAT RETURNS AN OBJECT
  // were going to use a lifecycle method- commonly where you would make http requests- 
  // in the created lifecylce method. When a component is loaded it goes through a lifecycle method which you can hook into with methods
  data() {
    return{
      // when created runs tasks array is filled
      tasks:[],
      showAddTask: false,
    }
 },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },

    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    
  deleteTask(id) {
    if(confirm('Are you sure?')) {
    // reset task - filter is a high order array method - takes in a  function loops thru
    // for each task we want to take the task id, where thats not equal to the id thats pased in above, thats what we ant back. We want everything back except the task with the id we passed in on the click method
      this.tasks = this.tasks.filter((task) => task.id !== id )
      }
    },
     toggleReminder(id){
      //  return an array of whatever we want - we want to return updated tasks
      // does the task.id equal the id thats passed in? if it is we want to return an array of objects with the initial task property
      // then we want to change the reminder to whatever the opposite is of the current reminder
      // else if it doesnt match the id we dont do anything
      this.tasks = this.tasks.map((task) => 
      task.id === id ? {...task, reminder: !task.reminder} : task)
    },


  },
  //lifecycle method
  //we pass this data to the tasks component
    created() {
      this.tasks = [

         {
          id:1, 
          text:"Doctors Appointment",
          day: 'March 1st at 2:30pm', 
          reminder: true,
        },

         {
          id:2, 
          text:"Meeting At Work",
          day: 'March 7th at 1:30pm', 
          reminder: false,
        },

         {
          id:3, 
          text:"Car Service",
          day: 'Friday the 18th at 8:15am', 
          reminder: true,
        },
          {
          id:4, 
          text:"Car Service",
          day: 'Friday the 18th at 8:15am', 
          reminder: true,
        },
          {
          id:5, 
          text:"Car Service",
          day: 'Friday the 18th at 8:15am', 
          reminder: true,
        },
          {
          id:6, 
          text:"Car Service",
          day: 'Friday the 18th at 8:15am', 
          reminder: true,
        },

      ] 
      }
   }

</script>

<style>
/* Global 
Styles */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}

</style>
