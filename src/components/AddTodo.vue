<template>
  

  <form action="">

      <input type="text" />
      <input type="submit" value="Thêm" class="add-btn" />
  </form>
</template>

<script>
export default {
    name: 'AddTodo',
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