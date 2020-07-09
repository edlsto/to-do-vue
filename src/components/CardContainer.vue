<template>
  <div class="card-container">
    <Card
      v-for="item in items"
      :key="item.key"
      :title="item.title"
      :description="item.description"
    />
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: {
    Card
  },
  name: "CardContainer",
  props: ["items"]
};
</script>

<style>
.card-container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  width: 80%;
  padding: 2em;
  grid-column-gap: 1em;
  background-color: #f3f6f7;
}
</style>
