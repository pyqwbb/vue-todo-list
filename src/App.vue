<template>
  <div class="todo">
    <TodoHeader :currentTab @update-tab="updateTabHandler" />
    <TodoList />
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
      console.log('완료');
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
