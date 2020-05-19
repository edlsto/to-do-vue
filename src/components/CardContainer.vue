<template>
  <div class="card-container">
    <div class="card" v-for="item in items" :key="item.key">
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

<style></style>
