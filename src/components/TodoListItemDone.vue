<template>
    <div>
        <span> {{ task.name }} </span>
        <button @click="task.done = !task.done">UnDone</button>
        <button @click="deleteTask">Delete</button>
    </div>
    
</template>
<script>
export default {
    name: 'TodoListItemDone',
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
<style scoped>
    span {
        text-decoration: line-through;
    }
</style>