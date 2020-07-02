<template>
  <div class="card-container">
    <div v-for="item in items" :key="item.key">
      <Card :title="item.title" :description="item.description" />
    </div>
  </div>
</template>

<script>
console.log("hi");
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
  margin: 2em;
  grid-column-gap: 1em;
}
</style>
