<template>
    <form @submit="addItem">
        <input type="text" placeholder="Việc mới" v-model="title"/>
        <input type="submit" value="Thêm" class="add-btn"/>
    </form>
</template>
<script>

import {ref} from 'vue'
// import {v4 as uuidv4} from 'uuid' // bỏ đi vì backend ko cần

export default ({
    name: 'AddTodo',
    setup(props, context) {
        const title = ref('')
        const addItem = event => {
            event.preventDefault()  //  để chống lại hành động mặc định của các form
            const newItem = {
                // id: uuidv4(), bỏ đi vì backend không cần
                title: title.value,
                completed: false
            }

            // Gửi tín hiệu
            context.emit('add-todo', newItem)
            title.value = ''
        }

        return {
            title,
            addItem
        }
    },
})
</script>
<style scoped>
form {
    display: flex;
}

input[type='text'] {
    flex: 10;
    padding: 5px;
}
input[type='submit'] {
    flex: 2;
}
</style>
