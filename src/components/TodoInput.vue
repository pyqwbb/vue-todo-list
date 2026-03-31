<template>
  <div class="todo__input">
    <input
      v-model="inputMsg"
      type="text"
      class="todo__input-text"
      placeholder="할 일을 입력하세요."
      @keydown.enter="addTodo"
    />
    <button class="todo__input-btn" @click="addTodo">등록</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const inputMsg = ref('');

const emit = defineEmits(['add-todo']);

const addTodo = () => {
  const trimmedMsg = inputMsg.value.trim();
  if (!trimmedMsg) return;

  emit('add-todo', trimmedMsg);
  inputMsg.value = '';
};
</script>
