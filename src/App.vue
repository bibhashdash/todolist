<template>
  <div class="app-wrapper">
    <h1>To Do List</h1>

    <!-- Form input to enter a task-->
    <!-- v-model to a temporary variable tempItem -->

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

    <!-- List container component  -->
    <!-- returns a list of all the tasks -->
    <!-- bind the list array and pass it as prop to Listcontainer.vue component -->
    <Listcontainer :list="list" />

    <!-- footer -->
    <!-- contains results -->
    <!-- also contains CLEAR LIST button -->

    <div class="footer">
      <!-- bind the list array and pass it as prop to Results component -->
      <Results :list="list" />
      <div class="clear-list" @click="clearList">
        <p>Clear List! <i class="fas fa-ban"></i></p>
      </div>
    </div>
  </div>
</template>

<script>
import Listcontainer from "./components/Listcontainer.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Listcontainer, Results },
  data() {
    return {
      // temp variable to store the user input
      tempItem: "",

      // array of all task items
      list: [],
    };
  },

  // handle page refresh
  //using mounted hook
  mounted() {
    const myStorage = window.localStorage;
    // console.log(myStorage);
    if (myStorage) {
      for (const [key, value] of Object.entries(myStorage)) {
        this.list.push(value);
      }
    }
  },
  methods: {
    addToList() {
      // add temp variable value to the top of task items array
      // unshift means it shows at the top of to do list
      this.list.unshift(this.tempItem);

      // generate random ID to allow local storage
      const randomID = Date.now();

      // add to local storage
      localStorage.setItem(randomID, this.tempItem);

      // clear temp variable
      this.tempItem = "";
    },

    // clear the list
    // also clears it from local storage
    clearList() {
      this.list = [];
      localStorage.clear();
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
  color: #fbf4f4;
  margin-top: 60px;
  width: 370px;
  /* border: 1px solid black; */
  background-color: #7c7c7c;
  border-radius: 10px;
}
h1,
h2 {
  padding: 10px 3px;
  font-family: "Montserrat", sans-serif;
}
h1 {
  font-weight: lighter;
}
h2 {
  font-size: 1rem;
  font-weight: lighter;
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
  /* gap: 0.5rem; */
}
input {
  border: none;
  /* border-bottom: 2px solid rgb(182, 182, 182); */
  font-family: "Quicksand", sans-serif;
  padding: 5px;
}
.icon {
  font-size: 1rem;
  /* margin-left: 10px; */
  cursor: pointer;
}
.submit {
  width: 29px;
  height: 26px;
  background-color: #4e4e4e;
  /* text-align: center; */
  display: flex;
  align-items: center;
  justify-content: center;
}
.submit:hover {
  background-color: #3adbd9;
}
.footer {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: center;
}
.clear-list {
  display: flex;
  padding: 5px 10px;
  justify-content: center;
  font-size: 1rem;
  border: 1px solid #fbf4f4;
  border-radius: 5px;
  cursor: pointer;
}
.clear-list p {
  margin: 0;
}
.clear-list:hover {
  background-color: #1f1e1e;
  color: #fff;
}
</style>
