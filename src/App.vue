<template>
  <div class="todo">
    <TodoHeader />
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
  },
};
</script>
