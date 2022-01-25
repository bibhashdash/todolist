<template>
  <div class="task">
    <p>
      <span :class="{ strikethrough: isTaskFinished }">{{ taskName }}</span>
    </p>
    <div class="action-buttons">
      <i class="fas fa-flag-checkered icon" @click="toggleTaskFinished"></i>
      <i class="fas fa-edit icon"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["taskName"],
  data() {
    return {
      isTaskFinished: false,
    };
  },
  methods: {
    toggleTaskFinished() {
      this.isTaskFinished = !this.isTaskFinished;
    },
  },
};
</script>

<style>
.task {
  display: grid;
  grid-template-columns: 70% auto;
  align-items: center;
}

.strikethrough {
  text-decoration: line-through;
}
</style>
