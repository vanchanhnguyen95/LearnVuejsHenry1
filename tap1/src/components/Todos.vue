<template>
<!-- <div class="todos">
    <p>Việc 1</p>
    <p>Việc 2</p>
    <p>Việc 3</p>
</div> -->
<!-- <p v-for="todo in todos" v-bind:key="todo.id">{{todo}}</p> -->
    <AddTodo @add-todo="addTodo"/>
    <TodoItem  
     v-for="todo in todos"
     :key="todo.id"
     :todoProps="todo"
     @item-completed="markItemComplete"
     @delete-item="deleteTodo"
     />
</template>
<script>
import { ref } from 'vue'
import {v4 as uuidv4} from 'uuid'

import TodoItem from './TodoItem'
import AddTodo from './AddTodo'

export default {
    name: 'Todos',
    components: {TodoItem, AddTodo},
    setup()
        {
        const todos = ref([
            {
                id: uuidv4(),
                title: ' Viec 1',
                completed: false
            },
            {
                id: uuidv4(),
                title: ' Viec 2',
                completed: false
            },
            {
                id: uuidv4(),
                title: ' Viec 3',
                completed: false
            },
            {
                id: uuidv4(),
                title: ' Viec 4',
                completed: false
            },
            {
                id: uuidv4(),
                title: ' Viec 5',
                completed: false
            },
            {
                id: uuidv4(),
                title: ' Viec 6',
                completed: false
            },
            {
                id: uuidv4(),
                title: ' Viec 7',
                completed: false
            }
        ])
        
        const markItemComplete = id => {
            // console.log(id)
            todos.value = todos.value.map(todo => {
                if(todo.id === id) todo.completed = !todo.completed
                return todo
            })
        }
        const deleteTodo = id => {
            todos.value = todos.value.filter(todo => todo.id !== id)
        }

        const addTodo = newTodo => {
            todos.value.push(newTodo)
        }

        return {
            todos,
            markItemComplete,
            deleteTodo,
            addTodo
        }
    }
}
</script>

<style scoped>
    /* .todos{
        text-align: left;
    } */
</style>