<template>
  <div class="results">
    <!-- <h2>Completed: {{ finalListISwear.length }}</h2> -->
    <!-- <h2>Pending: {{ pendingTally }}</h2> -->
    <h2 class="totalTally">Total: {{ list.length }}</h2>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: ["list", "completedTally"],
  data() {
    return {
      total: 0,
    };
  },
};
</script>

<style>
.results {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
/* .totalTally {
  color: #3ce7e4;
} */
</style>
