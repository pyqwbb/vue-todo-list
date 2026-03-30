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
import { ref } from 'vue';
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

    return {
      todo,
      currentTab,
      addTodoHandler,
      updateTodoHandler,
      deleteTodoHandler,
      editTodoHandler,
      updateTabHandler,
    };
  },
  // 컴포넌트가 생성될 때 실행되는 라이프사이클 훅 (초기 데이터 세팅에 사용)
  created() {
    // localStorage에 'todo'라는 key로 저장된 값을 가져옴 (문자열 형태)
    const saved = localStorage.getItem('todo');
    // 저장된 값이 존재할 경우에만 실행 (null 방지)
    if (saved) {
      // 문자열(JSON)을 자바스크립트 객체(배열)로 변환해서 todo에 넣어줌
      this.todo = JSON.parse(saved);
    }
  },
  // 특정 데이터(todo)가 변경되는 것을 감지해서 자동으로 실행되는 영역
  watch: {
    todo: {
      // todo 데이터가 변경될 때마다 실행되는 함수
      handler(newTodo) {
        // 변경된 todo 데이터를 문자열(JSON)로 변환해서 localStorage에 저장
        localStorage.setItem('todo', JSON.stringify(newTodo));
      },
      // 배열이나 객체 내부 값까지 감지하기 위한 deep 옵션
      deep: true,
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
