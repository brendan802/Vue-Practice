<template>
<div>
    <div :key="task.id" v-for="task in tasks">
        <!-- the task data is still a level up so we need to emit AGAIN! with same method -->
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />
    </div>  
</div>
</template>

<script>
import Task from './Task.vue'

export default {
    name:'Tasks',
    props: {
        tasks:Array
    },
    components: {
        Task,
    },
    emits: ['delete-task', 'toggle-reminder'],
}
</script>