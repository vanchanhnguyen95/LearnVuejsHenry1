<template>
    <!-- <p class="todo-item is-completed" :id="new_id">
        <input type="checkbox"/>
        {{todoProps.title}}
        <button class="btn btn-primary del-btn">Delete</button>
    </p> -->
    <p :class="['todo-item',todoProps.completed ? 'is-completed' : '']" :id="new_id">
        <input type="checkbox"  :checked="todoProps.completed" @change="markItemCompleted"/>
        {{todoProps.title}}
        <button class="btn btn-primary del-btn" @click="deleteItem">Delete</button>
    </p>
</template>
<script>
// import { ref } from 'vue'
export default {
    name: 'TodoItem',
    props: ['todoProps'],
    setup(props, context) {
        // const new_id = ref('my-new-id')
        // return {
        //     new_id
        // }
        const markItemCompleted = () => {
            context.emit('item-completed', props.todoProps.id)
        }
        const deleteItem = () => {
            context.emit('delete-item', props.todoProps.id)
        }
        return {
            markItemCompleted,
            deleteItem
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