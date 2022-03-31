<template>
    <TodoItem v-for="todo in TodoList" v-bind:key="todo.id" v-bind:todoProps = "todo"/>
</template>

<script>
import { ref } from '@vue/reactivity'
import TodoItem from './TodoItem.vue'

export default {
    name: 'TodoList',
    components:{
        TodoItem 
    },
    setup(){
        const TodoList = ref([
            {
                id: 1,
                title: "viec 1",
                complete: false
            },
            {
                id: 2, 
                title: "viec 2",
                complete: false
            },
            {
                id: 3,
                title: "viec 3",
                complete: false
            }, 
        ])
        return {
            TodoList
        }
    }
}
</script>

<style>

</style>