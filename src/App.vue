<template>
  <div class="todo">
    <TodoHeader :currentTab @update-tab="updateTabHandler" />
    <TodoList
      :computedTodo="computedTodo"
      @update-todo="updateTodoHandler"
      @delete-todo="deleteTodoHandler"
      @edit-todo="editTodoHandler"
    />
    <TodoInput @add-todo="addTodoHandler" />
  </div>
</template>

<script>
import { ref, computed, watch, onMounted } from 'vue';
import TodoHeader from './components/TodoHeader.vue';
import TodoList from './components/TodoList.vue';
import TodoInput from './components/TodoInput.vue';

export default {
  components: { TodoHeader, TodoList, TodoInput },

  setup() {
    const todo = ref([]);
    const currentTab = ref('all');

    const addTodoHandler = (inputMsg) => {
      const item = {
        id: Math.random(),
        msg: inputMsg,
        completed: false,
      };
      todo.value.push(item);
    };

    const updateTodoHandler = (id) => {
      todo.value = todo.value.map((v) =>
        v.id === id ? { ...v, completed: !v.completed } : v,
      );
    };

    const deleteTodoHandler = (id) => {
      todo.value = todo.value.filter((v) => v.id !== id);
    };

    const editTodoHandler = ({ id, msg }) => {
      todo.value = todo.value.map((v) => (v.id === id ? { ...v, msg } : v));
    };

    const updateTabHandler = (tab) => {
      currentTab.value = tab;
    };

    const computedTodo = computed(() => {
      if (currentTab.value === 'all') {
        return todo.value;
      } else {
        return todo.value.filter((v) => v.completed);
      }
    });

    watch(
      todo,
      (newTodo) => {
        localStorage.setItem('todo', JSON.stringify(newTodo));
      },
      { deep: true },
    );

    onMounted(() => {
      const saved = localStorage.getItem('todo');
      if (saved) {
        todo.value = JSON.parse(saved);
      }
    });

    return {
      todo,
      currentTab,
      computedTodo,
      addTodoHandler,
      updateTodoHandler,
      deleteTodoHandler,
      editTodoHandler,
      updateTabHandler,
    };
  },
};
</script>
