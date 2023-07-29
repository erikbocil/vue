<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <h1>Todo List{{ todos.length > 1 ? 's' : '' }}</h1>
    <ol>
      <TodoList
        v-for="(todo, index) in todos"
        :key="index"
        :index="index"
        :todo="todo"
        @edit-to-do="editTodo"
        @delete-to-do="deleteTodo"
        @update-to-do="updateTodo"
      />
    </ol>
    <!-- <ol>
      <li v-for="(todo, index) in todos" :key="index">
        <template v-if="todo.editing">
          <input type="text" v-model="todo.todo" />
          <button @click="updateTodo(index, todo.todo)">Update</button>
        </template>
        <template v-else>
          <span>{{ todo }}</span>
          <button @click="editTodo(index)">Edit</button>
          <button @click="deleteTodo(index)">Delete</button>
        </template>
      </li>
    </ol> -->
    <input
      type="text"
      v-model="todo"
      @keyup.enter="addTodo"
      style="width: 80%"
    />
    <button @click="addTodo">Tambahkan</button>
    <p v-if="hebat">Hebat!</p>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TodoList from '@/components/TodoList.vue';
export default {
  name: 'App',
  components: {
    // HelloWorld
    TodoList,
  },
  data() {
    return {
      todos: [],
      todo: '',
    };
  },
  methods: {
    addTodo: function () {
      if (this.todo.trim() === '') {
        return;
      }
      this.todos.push({ todo: this.todo, editing: false });
      this.todo = '';
    },
    editTodo: function (index) {
      this.todos[index].editing = !this.todos[index].editing;
    },
    deleteTodo: function (index) {
      this.todos.splice(index, 1);
    },
    updateTodo: function (index, todo) {
      this.todos[index].editing = !this.todos[index].editing;
      this.todos[index].todo = todo;
    },
  },
  computed: {
    hebat: function () {
      return this.todos.length > 3;
    },
  },
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
