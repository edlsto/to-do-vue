<template>
  <div class="card">
    <div class="title">{{ title }}</div>
    <div class="description">{{ description }}</div>
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
  border: 1px solid black;
}
</style>
