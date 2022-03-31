<template>

    <AddTodo />
    <TodoItem 
    v-for="todo in TodoList" 
    v-bind:key="todo.id" 
    v-bind:todoProps = "todo"
    v-on:item-completed="markItemCompleted"
    v-on:delete-item="deleteTodo"
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
        AddTodo
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
            TodoList.value = TodoList.value.map(todo =>{
                if (todo.id === id) todo.completed = !todo.completed;
                return todo
            })
            console.log(id)
        }

        const deleteTodo = id => {
            TodoList.value = TodoList.value.filter(todo => todo.id !== id)
        }
        return {
            TodoList,
            markItemCompleted,
            deleteTodo
        }
    }
}
</script>

<style>

</style>