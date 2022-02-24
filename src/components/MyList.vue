<template>
  <ul class="todo-main">
    <!-- 
      将从App.vue中传入的todos循环到循环存到todoObj中
      绑定Key值，因为id是唯一的，所以绑定todoObj.id
      将todoObj传到MyItem中
     -->
    <MyItem
      v-for="todoObj in todos"
      :key="todoObj.id"
      :todo="todoObj"
      :checkTodo="checkTodo"
      :deleteTodo="deleteTodo"
    />
  </ul>
</template>

<script>
import MyItem from "./MyItem.vue";
export default {
  name: "MyList",
  components: { MyItem },
  props: ["todos", "deleteTodo", "checkTodo"],
};
</script>

<style scoped>
/*main*/
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
