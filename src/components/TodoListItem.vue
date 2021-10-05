<template>
    <div>
        <span> {{ task.name }} </span>
        <button class="done" @click="task.done = !task.done"> Done</button>
        <button class="delete" @click="deleteTask">Delete</button>
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
<style scoped>
    .done {
        background-color: #d1d1d1;
    }
</style>