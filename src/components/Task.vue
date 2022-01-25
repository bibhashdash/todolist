<template>
  <div class="task">
    <p>
      <span :class="{ strikethrough: isTaskFinished }">{{ taskName }}</span>
    </p>
    <div class="action-buttons">
      <i class="fas fa-flag-checkered icon" @click="toggleTaskFinished"></i>
      <i class="fas fa-edit icon" @click="editTaskName"></i>
      <i class="fas fa-trash icon" @click="deleteTask"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["taskName", "list"],
  data() {
    return {
      isTaskFinished: false,
    };
  },
  methods: {
    toggleTaskFinished() {
      this.isTaskFinished = !this.isTaskFinished;
    },
    deleteTask() {
      const taskNameIndex = this.list.indexOf(this.taskName);
      this.list.splice(taskNameIndex, 1);
      console.log(this.list);
    },
    editTaskName() {
      const taskNameIndex = this.list.indexOf(this.taskName);
      let tempName = prompt("New name");
      this.list.splice(taskNameIndex, 1, tempName);
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
  text-decoration-color: red;
}
</style>
