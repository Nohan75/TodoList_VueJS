<template>
    <div>
        <h1>Todo List</h1>
        <input v-model="task">
        <button @click="addTask">Add</button>
        <ul>
            <li v-for="(elem, index) in tasks" :key="index">
                <TodoListItem
                    v-show="!elem.done"
                    :tasks="tasks"
                    :task="elem"
                    @delete="deleteTask(index)"
                />

                <TodoListItemDone
                    v-show="elem.done"
                    :tasks="tasks"
                    :task="elem"
                    @delete="deleteTask(index)"
                />
                
            </li>
            
        </ul>
    </div>
</template>
<script>
import TodoListItem from './TodoListItem.vue'
import TodoListItemDone from './TodoListItemDone.vue'
export default {
  components: { TodoListItem, TodoListItemDone },
    name: 'TodoList',
    data() {
        return {
            task: "",
            tasks: [],
        }
    },
    methods: {
        addTask() {
            if(this.task !== ""){
                this.tasks.push({
                    name: this.task,
                    done: false,
                });
                this.task = '';
            }
            
        },
        deleteTask(index) {
            this.tasks.splice(index, 1);
        },
    }
    
    
}
</script>
<style>
    li {
        list-style: none;
    }
    
</style>