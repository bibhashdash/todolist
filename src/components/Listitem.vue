<template>
  <ul>
    <li class="list-item" v-for="item in list" :key="item">
      {{ item }} <i class="fas fa-flag-checkered icon"></i>
      <i class="fas fa-edit icon"></i>
      <i class="far fa-trash-alt icon"></i>
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
export default {
  name: "Listitem",
  props: ["list", "itemShowing"],
  methods: {},
};
</script>

<style>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
  margin: 10px 0 20px;
  padding: 0;
}
.hidden {
  display: none;
}

.list-item {
  display: grid;
  grid-template-columns: 70% 10% 10% 10%;
}
</style>
