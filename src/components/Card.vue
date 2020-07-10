<template>
  <div class="card">
    <div class="title">{{ title }}</div>
    <div class="item-container">
      <img class="checkbox" src="../assets/checkbox.svg" />
      <div class="description">{{ description }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: ["title", "description"]
};
</script>

<style>
.card {
  border: 1px solid #c7d3d8;
  padding: 0.2em;
  background-color: #fafdff;
  margin-bottom: 1em;
}
.title {
  font-weight: bold;
  padding: 0.3em 1em;
}

.checkbox {
  height: 1em;
  margin-right: 0.5em;
  margin-top: 0.25em;
}

.item-container {
  display: flex;
  border-top: 1px solid #c7d3d8;
  padding: 0.7em 1em;
}
</style>
