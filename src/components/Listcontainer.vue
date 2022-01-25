<template>
  <ul class="list-container">
    <li v-for="taskName in list" :key="taskName">
      <Task :taskName="taskName" :list="list" />
    </li>
  </ul>

  <!-- <div class="modal hidden">
    <div class="modal-background">
      <div class="modal-content">
        <h1>Alert</h1>
        <h2>Delete task, are you sure?</h2>
        <div class="modal-buttons">
          <i class="fas fa-check-square icon"></i>
          <i class="fas fa-times icon"></i>
        </div>
      </div>
    </div>
  </div> -->
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "Listcontainer",
  props: ["list"],
  components: {
    Task,
  },
};
</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.list-container {
  width: 300px;
  height: 500px;
  overflow-y: scroll;
}
li {
  list-style: none;
  margin: 10px 0 20px;
  padding: 0;
}
.hidden {
  display: none;
}
</style>
