<template>
  <div class="todo__title">
    <h1 class="todo__text">Todo List</h1>
    <ul class="todo__tab">
      <li
        :class="{ 'todo__tab--active': currentTab === 'all' }"
        @click="updateTab('all')"
      >
        전체
      </li>
      <li
        :class="{ 'todo__tab--active': currentTab === 'completed' }"
        @click="updateTab('completed')"
      >
        완료
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    currentTab: {
      type: String,
      default() {
        return 'all';
      },
    },
  },
  emits: ['update-tab'],
  methods: {
    updateTab(currentTab) {
      this.$emit('update-tab', currentTab);
    },
  },
};
</script>
