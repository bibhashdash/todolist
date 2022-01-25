<template>
  <div class="app-wrapper">
    <h1>To Do List</h1>
    <form @submit.prevent="addToList" class="task-input">
      <input
        placeholder="Enter task..."
        type="text"
        v-model="tempItem"
        required
      />
      <div @click="addToList" class="submit">
        <i class="fas fa-arrow-right icon"></i>
      </div>
    </form>
    <Listcontainer :list="list" />
  </div>
</template>

<script>
import Listcontainer from "./components/Listcontainer.vue";

export default {
  name: "App",
  components: { Listcontainer },
  data() {
    return {
      tempItem: "",
      list: [],
    };
  },

  methods: {
    addToList() {
      this.list.push(this.tempItem);
      this.tempItem = "";
      // console.log(this.list);

      // to do: Validation and empty inputs
    },
  },
};
</script>

<style>
#app {
  font-family: "Quicksand", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #2c3e50;
  margin-top: 60px;
}
form {
  width: 300px;
  display: grid;
  grid-template-columns: 90% 10%;
}
.task-input {
  display: grid;
  grid-template-columns: 90% 10%;
  align-items: center;
}
input {
  border: none;
  border-bottom: 2px solid rgb(182, 182, 182);
  font-family: "Quicksand", sans-serif;
  padding: 5px;
}
.icon {
  font-size: 1rem;
  margin-left: 10px;
  cursor: pointer;
}
</style>
