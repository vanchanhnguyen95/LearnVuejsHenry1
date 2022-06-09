<template>
<!-- <div class="todos">
    <p>Việc 1</p>
    <p>Việc 2</p>
    <p>Việc 3</p>
</div> -->
<!-- <p v-for="todo in todos" v-bind:key="todo.id">{{todo}}</p> -->
    <TodoItem  v-for="todo in todos" v-bind:key="todo" v-bind:todoProps="todo"/>
</template>
<script>
import { ref } from 'vue'

import TodoItem from './TodoItem'

export default {
    name: 'Todos',
    components: {TodoItem},
    setup()
        {
        const todos = ref(['Viec 1','Viec 2','Viec 3'])

        return {
            todos
        }
    }
}
</script>

<style scoped>
    .todos{
        text-align: left;
    }
</style>