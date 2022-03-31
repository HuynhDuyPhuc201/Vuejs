<template>

    <AddTodo 
        @add-todo="addTodo"
    />
    <TodoItem 
        v-for="todo in TodoList" 
        :key="todo.id" 
        :todoProps = "todo"
        @item-completed="markItemCompleted"
        @delete-item="deleteTodo"
    />
    <!-- v-bind = :,   v-on: @  -->
</template>

<script>
import { ref } from '@vue/reactivity'
import TodoItem from './TodoItem.vue'
import AddTodo from './AddTodo.vue'
// import { v4 as uuidv4 } from 'uuid';
import axios from 'axios'  // import dữ liệu từ trang web https://jsonplaceholder.typicode.com/todos

export default {
    name: 'TodoList',
    components:{
        TodoItem,
        AddTodo,
    },
    setup(){
        const TodoList = ref([]);

        const getAllTodos = async () =>{    // hàm bất đồng bộ
            try {
                const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')  // ?_limit=10  : lấy 10 data
                TodoList.value = res.data  // đưa dữ liệu từ res mới khai báo sang TodoList ref
                // console.log(res.data)
            } catch (error) {
                console.log(error) // nếu có vấn đề gì thì chỉ cần log nó ra
            }
        }               
        getAllTodos()


        const markItemCompleted = id => {
            TodoList.value = TodoList.value.map(todo => {
                if(todo.id === id) todo.completed = !todo.completed
                return todo
            })
        }

        const deleteTodo = id => {
            TodoList.value = TodoList.value.filter(todo => todo.id !== id)
        }

        const addTodo = newTodo => {
            console.log(newTodo.id)
            TodoList.value.push(newTodo)
        }
        return {
            TodoList,
            markItemCompleted,
            deleteTodo,
            addTodo,
        }
    }
}
</script>

<style>

</style>