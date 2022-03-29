<template>
    <TodoItem v-for="todo in TodoList" v-bind:key="todo" v-bind:todoProps = "todo"/>
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
            'viec 1 ',
            'viec 2 ',
            'viec 3 ',
        ])
        return {
            TodoList
        }
    }
}
</script>

<style>

</style>