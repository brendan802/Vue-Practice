<template>
<!-- button element, btn class, inline bind color which pulls from app.vue, text is also pulled from header.vue -->
    <button @click ="onClick()" v-bind:style="{background: color}" class="btn">{{text}}</button>
</template>

<script>
// export button component
    export default {
        name:'Button',
        // prop values of button
        props:{
            text: String,
            color: String
        },
        // onclick function for button compoenent
        methods:{
            onClick(){
                this.$emit('toggle-add-task')
                console.log("works")
        }
        }
    }
</script>
