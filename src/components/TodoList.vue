<template>

    <AddTodo />
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

export default {
    name: 'TodoList',
    components:{
        TodoItem,
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

        // const markItemCompleted = id => {
        //     TodoList.value = TodoList.value.map(todo =>{
        //         if (todo.id === id) todo.completed = !todo.completed;
        //         return todo
        //     })
        //     console.log(id)
        // }
        const markItemCompleted = id => {
            TodoList.value = TodoList.value.map(todo => {
                if(todo.id === id) todo.completed = !todo.completed
                return todo
            })
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