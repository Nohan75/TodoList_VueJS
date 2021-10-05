<template>
    <div>
        <span> {{ task.name }} </span>
        <button @click="task.done = !task.done"> Done</button>
        <button @click="deleteTask">Delete</button>
    </div>
</template>
<script>
export default {
    name: 'TodoListItem',
    props: {
        task: Object,
    },
    methods: {
        deleteTask() {
            this.$emit('delete');
        }
    }
}
</script>
<style>
    
</style>