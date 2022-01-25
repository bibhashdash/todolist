<template>
  <div class="results">
    <h2>Completed: {{ completedTally }}</h2>
    <h2>Pending: {{ pendingTally }}</h2>
    <h2>Total: {{ list.length }}</h2>
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
  methods: {},
};
</script>

<style>
.results {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
