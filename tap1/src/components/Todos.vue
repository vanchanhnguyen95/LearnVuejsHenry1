<template>
<!-- <div class="todos">
    <p>Việc 1</p>
    <p>Việc 2</p>
    <p>Việc 3</p>
</div> -->
<!-- <p v-for="todo in todos" v-bind:key="todo.id">{{todo}}</p> -->
    <TodoItem  v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo"/>
</template>
<script>
import { ref } from 'vue'

import TodoItem from './TodoItem'

export default {
    name: 'Todos',
    components: {TodoItem},
    setup()
        {
        const todos = ref([
            {
                id: 1,
                title: ' Viec 1',
                completed: false
            },
            {
                id: 2,
                title: ' Viec 2',
                completed: false
            },
            {
                id: 3,
                title: ' Viec 3',
                completed: false
            },
            {
                id: 4,
                title: ' Viec 4',
                completed: true
            },
            {
                id: 5,
                title: ' Viec 5',
                completed: true
            },
            {
                id: 6,
                title: ' Viec 6',
                completed: false
            },
            {
                id: 7,
                title: ' Viec 7',
                completed: true
            }
            ])

        return {
            todos
        }
    }
}
</script>

<style scoped>
    /* .todos{
        text-align: left;
    } */
</style>