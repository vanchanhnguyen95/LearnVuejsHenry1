<template>
    <!-- <p class="todo-item is-completed" :id="new_id">
        <input type="checkbox"/>
        {{todoProps.title}}
        <button class="btn btn-primary del-btn">Delete</button>
    </p> -->
    <p :class="['todo-item',todoProps.completed ? 'is-completed' : '']" :id="new_id">
        <input type="checkbox"  :checked="todoProps.completed"/>
        {{todoProps.title}}
        <button class="btn btn-primary del-btn">Delete</button>
    </p>
</template>
<script>

import { ref } from 'vue'
export default {
    name: 'TodoItem',
    props: ['todoProps'],
    setup() {
        const new_id = ref('my-new-id')
        return {
            new_id
        }
    },
}
</script>
<style scoped>
.is-completed {
    text-decoration: line-through;
}
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px #ccc dotted;
}
.del-btn {
    background: #ff0000;
    color: #fff;
    border: none;
    cursor: pointer;
    float: right;
}
</style>