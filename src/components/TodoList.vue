<template>
  <div class="todo__list">
    <!-- 할 일 목록이 있을 때 (완료 시 .todo__item--completed 클래스 추가 )-->
    <div
      class="todo__item"
      v-for="item in computedTodo"
      :key="item.id"
      :class="{ 'todo__item--completed': item.completed }"
    >
      <input
        type="checkbox"
        :id="item.id"
        :checked="item.completed"
        @click="updateTodo(item.id)"
      />
      <label :for="item.id" class="todo__checkbox-label"></label>
      <span v-if="editingId !== item.id" class="todo__item-text">
        {{ item.msg }}
      </span>
      <input
        v-else
        v-model="editingMsg"
        type="text"
        @keydown.enter="saveEdit(item.id)"
        autofocus
      />
      <span
        class="material-symbols-outlined todo__edit-icon"
        @click="editTodo(item)"
      >
        edit
      </span>
      <span
        class="material-symbols-outlined todo__delete-icon"
        @click="deleteTodo(item.id)"
      >
        delete
      </span>
    </div>
    <!-- 할 일 목록이 없을 때 -->
    <div v-if="computedTodo.length === 0" class="todo__item--no">
      <p>할일 목록이 없습니다.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editingId: null,
      editingMsg: '',
    };
  },
  props: {
    computedTodo: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  emits: ['update-todo', 'delete-todo', 'edit-todo'],
  methods: {
    updateTodo(id) {
      this.$emit('update-todo', id);
    },
    deleteTodo(id) {
      this.$emit('delete-todo', id);
    },
    editTodo(item) {
      this.editingId = item.id;
      this.editingMsg = item.msg;
    },
    saveEdit(id) {
      this.$emit('edit-todo', { id, msg: this.editingMsg });
      this.editingId = null;
      this.editingMsg = '';
    },
  },
};
</script>
