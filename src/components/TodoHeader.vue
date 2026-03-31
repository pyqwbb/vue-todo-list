<template>
  <div class="todo__title">
    <h1 class="todo__text lilita-one-regular">To Do List</h1>
    <div class="todo__tab">
      <p
        :class="{ 'todo__tab--active': currentTab === 'all' }"
        @click="updateTab('all')"
      >
        전체 {{ completedCount + remainingCount }}개
      </p>
      <p
        :class="{ 'todo__tab--active': currentTab === 'remaining' }"
        @click="updateTab('remaining')"
      >
        남은 일 {{ remainingCount }} 개
      </p>
      <p
        :class="{ 'todo__tab--active': currentTab === 'completed' }"
        @click="updateTab('completed')"
      >
        완료 {{ completedCount }}개
      </p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  currentTab: {
    type: String,
    default: 'all',
  },
  completedCount: {
    type: Number,
  },
  remainingCount: {
    type: Number,
  },
});

const emit = defineEmits(['update-tab']);

const updateTab = (tab) => {
  emit('update-tab', tab);
};
</script>
