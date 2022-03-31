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

export default {
    name: 'TodoList',
    components:{
        TodoItem,
        AddTodo,
    },
    setup(){
        const TodoList = ref([
            {
                id: 1,
                title: "viec 1",
                completed: false
            },
            {
                id: 2, 
                title: "viec 2",
                completed: false
            },
            {
                id: 3,
                title: "viec 3",
                completed: false
            }, 
        ])

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
            addTodo
        }
    }
}
</script>

<style>

</style>