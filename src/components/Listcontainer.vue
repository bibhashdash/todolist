<template>
  <!-- contains the list of tasks // returns the full list each render -->
  <ul class="list-container">
    <!-- output a dynamic list using v-for -->
    <!-- Using List array received as prop -->
    <!-- This is in lieu of a data property below -->
    <!-- SO the list array IS the data -->
    <!-- Ergo can be iterated upon and rendered -->
    <li v-for="taskName in list" :key="taskName">
      <!-- Use Task component to render each individual task -->
      <!-- Passing iteration variable taskName into Task.vue component -->
      <!-- Also passing entire list array into Task.vue component -->
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

  // Receive List array as a prop from App.vue
  props: ["list"],
  components: {
    // receive Task as a component
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
  margin-top: 1rem;
  border-bottom: 2px solid #fbf4f496;
  /* border-radius: 10px; */
  width: 300px;
  height: 400px;
  overflow-y: scroll;
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.list-container::-webkit-scrollbar {
  display: none;
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
