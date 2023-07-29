<template>
  <li>
    <template v-if="todo.editing">
      <input type="text" v-model="update" />
      <button @click="$emit('update-to-do', index, update)">Update</button>
    </template>
    <template v-else>
      <p style="width: 80%; display: inline-block">{{ todo.todo }}</p>
      <button @click="$emit('edit-to-do', index)">Edit</button>
      <button @click="$emit('delete-to-do', index)">Delete</button>
    </template>
  </li>
</template>

<script>
export default {
  props: {
    todo: Object,
    index: Number,
  },
  data() {
    return {
      update: this.todo.todo,
    };
  },
};
</script>
