<template>
  <p :class="['todoItem', todoProps.completed ? 'is-completed' : '']">
      <input 
      type="checkbox" 
      :checked="todoProps.completed" 
      @:change="markItemCompleted()"
      />
      {{ todoProps.title }}
      <button class="del-btn" @click="deleteItem()">Delete</button>
  </p>
</template>

<script>
// import { ref } from '@vue/reactivity'

export default {
    name: 'TodoItem',
    props: ['todoProps'],
    setup(props, context){
      const markItemCompleted = () => {
        // console.log(props.todoProps)
        context.emit('item-completed', props.todoProps.id);
      }

      const deleteItem = () => {
        context.emit('delete-item', props.todoProps.id)
      }


      return{
        markItemCompleted,
        deleteItem
      }
    }
}
</script>

<style>

.is-completed  {
  text-decoration: line-through;
}

.del-btn{
  background: #ff0000;
  color: #fff;
  cursor: pointer;
  float: right;
}

</style>