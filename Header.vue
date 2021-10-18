<template>
    <header>
        <!-- h1 string pulled from app.vue -->
        <h1> {{ title }}</h1>
        <!-- Button component , change text or color from here -->
        <Button @toggle-add-task="$emit
        ('toggle-add-task')" 
        :text ="showAddTask ? 'Close' : 'Add Task'" 
        :color="showAddTask ? 'red' : 'green'"/>
     </header>
</template>

<script>
// import button component
import Button from './Button'
    // export components to be used by app.vue
    export default {
        name:'Header',
        props:{
            title: String,
            showAddTask: Boolean,

        },
        // export button 
        components: {
            Button,
          
            }
        
        }
</script>


<style scoped>
/* style is scoped to file */
    header {
        display:flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
        }
</style>
