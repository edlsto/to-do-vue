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

<style></style>
