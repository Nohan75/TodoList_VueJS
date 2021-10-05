<template>
    <div>
        <h1>Todo List</h1>
        <input v-model="task" placeholder="Saisissez une tâche">
        <button class="add-button" @click="addTask">Add</button>
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

    input {
        border-style: none;
        background-color: #F4F6F8;
        padding: 15px 10px;
        border-radius: 5px;
        width: 250px;
    }
    button{
        min-width: 70px;
        height: 40px;
        margin-left: 40px;
        border-style: none;
        border-radius: 4px;
        background-color: #d1d1d1;
        font-size: 18px;
        cursor: pointer;
    }
    span {
        font-size: 20px;
    }
    .done {
        background-color: #d1d1d1;
    }
    
</style>