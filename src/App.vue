<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <!-- 与MyHeader中的addTodo方法建立连接 -->
        <MyHeader :addTodo="addTodo" />
        <!-- 
          将App中的todos对象传到MyList中
          
           -->
        <MyList
          :todos="todos"
          :deleteTodo="deleteTodo"
          :checkTodo="checkTodo"
        />
        <MyFooter
          :todos="todos"
          :checkAllTodo="checkAllTodo"
          :clearAllTodo="clearAllTodo"
        />
      </div>
    </div>
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import MyList from "./components/MyList.vue";
import MyFooter from "./components/MyFooter.vue";

export default {
  // 组件的名称
  name: "App",
  // 注册组件
  components: {
    MyHeader,
    MyList,
    MyFooter,
  },
  data() {
    return {
      todos: [
        { id: "001", title: "抽烟", done: true },
        { id: "002", title: "喝酒", done: false },
        { id: "003", title: "开车", done: true },
      ],
    };
  },
  methods: {
    // 将用户在输入框中输入的内容存到todos中，
    addTodo(todoObj) {
      this.todos.unshift(todoObj);
    },
    checkTodo(id) {
      this.todos.forEach((todo) => {
        if (todo.id === id) todo.done = !todo.done;
      });
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== id;
      });
    },
    checkAllTodo(done) {
      this.todos.forEach((todo) => {
        todo.done = done;
      });
    },
    clearAllTodo() {
      this.todos = this.todos.filter((todo) => {
        return !todo.done;
      });
    },
  },
};
</script>

<style scoped>
/* 全局样式 */
/*base*/
body {
  background: #fff;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
