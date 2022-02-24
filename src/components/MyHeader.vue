<template>
  <div class="todo-header">
    <!-- 
      将用户输入的内同用双向绑定存到title中
      当用户按回车键时触发add事件
       -->
    <input
      type="text"
      placeholder="请输入你的任务名称，按回车键确认"
      v-model="title"
      @keyup.enter="add"
    />
  </div>
</template>

<script>
// 第三方库，自动生成id
import { nanoid } from "nanoid";
export default {
  name: "MyHeader",
  // 注册组件间通信，addTodo与App.vue间的通信
  props: ["addTodo"],
  data() {
    return {
      // 存放用户在输入框中输入的内容
      title: "",
    };
  },
  methods: {
    // add函数，当用户敲击回车键的时候触发
    add() {
      // 判断用户是否有在输入框中输入内容，若没有，提示用户
      if (!this.title.trim()) return alert("输入不能为空");
      // 将用户输入的数据存放到todoObj中
      const todoObj = { id: nanoid(), title: this.title, done: false };
      // 调用从App.vue中传入的addTodo()方法，作用是将用户输入的内容存到App.vue中的todos中
      this.addTodo(todoObj);
      // 当数据存到App.vue中的todos时，输入框变为空
      this.title = "";
    },
  },
};
</script>

<style scoped>
/*header*/
.todo-header input {
  width: 560px;
  height: 28px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  padding: 4px 7px;
}

.todo-header input:focus {
  outline: none;
  border-color: rgba(82, 168, 236, 0.8);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075),
    0 0 8px rgba(82, 168, 236, 0.6);
}
</style>
