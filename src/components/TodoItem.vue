<template>
  <p :class="['todoItem', ]">
      <input type="checkbox" />
      {{ todoProps.title }}
      <button class="del-btn">Delete</button>
  </p>
</template>

<script>
import { ref } from '@vue/reactivity'
export default {
    name: 'TodoItem',
    props: ['todoProps'],
    setup(){
      const new_id = ref('my-new-id')
      return{
        new_id
      }
    }
}
</script>

<style>

.is-complete  {
  text-decoration: line-through;
}

.del-btn{
  background: #ff0000;
  color: #fff;
  cursor: pointer;
  float: right;
}

</style>