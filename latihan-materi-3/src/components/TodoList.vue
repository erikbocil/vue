<script>
export default {
  name: 'TodoList',
  data() {
    return {
      todo: '',
      todos: [],
    };
  },
  methods: {
    addTodo: function () {
      this.todos.push(this.todo);
      this.todo = '';
    },
  },
  computed: {
    hebat: function () {
      return this.todos.length > 3;
    },
  },
};
</script>

<template>
  <div>
    <ol>
      <li v-for="(todo, index) in todos" :key="index">{{ todo }}</li>
    </ol>
    <input type="text" v-model="todo" />
    <button @click="addTodo">Tambahkan</button>
    <p v-if="hebat">Hebat</p>
  </div>
</template>
