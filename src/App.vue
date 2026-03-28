<template>
  <div class="todo">
    <TodoHeader :currentTab @update-tab="updateTabHandler" />
    <TodoList :computedTodo="computedTodo" @update-todo="updateTodoHandler" />
    <TodoInput @add-todo="addTodoHandler" />
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoList from './components/TodoList.vue';
import TodoInput from './components/TodoInput.vue';

export default {
  components: { TodoHeader, TodoList, TodoInput },
  data() {
    return {
      todo: [],
      currentTab: 'all',
    };
  },
  methods: {
    addTodoHandler(inputMsg) {
      const item = {
        id: Math.random(),
        msg: inputMsg,
        completed: false,
      };
      this.todo.push(item);
    },
    updateTodoHandler(id) {
      this.todo = this.todo.map((v) =>
        v.id === id ? { ...v, completed: !v.completed } : v,
      );
    },
    updateTabHandler(tab) {
      this.currentTab = tab;
    },
  },
  computed: {
    computedTodo() {
      if (this.currentTab === 'all') {
        return this.todo;
      } else {
        return this.todo.filter((v) => v.completed);
      }
    },
  },
};
</script>
