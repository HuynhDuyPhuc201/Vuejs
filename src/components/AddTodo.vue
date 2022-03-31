<template>
  

  <form action="" @submit="addItem">
      <!-- v-model: gán -->
      <input type="text" placeholder="Thêm vào..." v-model="title"/> 
      <input type="submit" value="Thêm" class="add-btn" />
  </form>
</template>

<script>
import { ref } from '@vue/reactivity'

import { v4 as uuidv4 } from 'uuid';


export default {
    name: 'AddTodo',
    setup(grops, context ){  // nhập context, vì context là tham số thứ 2 nên phải thêm grops vào, mặc dù kh dùng tới nó
        const title = ref('')  // title: lưu trữ giá trị người dùng nhập vào (trạng thái khởi điểm là rỗng)

        const addItem = (e) => {
            e.preventDefault();
            
            // tạo 1 công việc mới
            const newItem = {
                id: uuidv4(),
                title: title.value,
                completed: false
            }

            context.emit('add-todo', newItem)

            title.value = ' '
        }
        return{
            title,
            addItem
        }
    }
}
</script>

<style scoped>
form{
    display: flex;
}
input[type='text']{
    flex: 10;
    padding: 5px;
}
input[type='submit']{
    flex: 2;
}


</style>>