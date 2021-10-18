<template>

<!--task.reminder terniary if that is true add 'reminder' comma, we also want the task class  -->
<div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3  > {{ task.text }} 
        <!-- Click Icon - MEthod takes the task id -->
        <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
    </h3>
    <p  >  {{ task.day}} </p>
</div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object,
    },
    // Define the onclick method for delete -- We need to emit upwards into the App.vue (this.$emit) -- need to catch emit next level up in Tasks.vue
    methods:{
       
    }
}
</script>

<style scope>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border: 5px solid rgb(21, 236, 165);
  
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>