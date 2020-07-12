<template>
  <div class="wrapper">
    <div class="card-container">
      <Card
        v-for="item in items"
        v-bind:key="item.key"
        v-bind:title="item.title"
        v-bind:tasks="item.tasks"
        v-bind:id="item.id"
        v-bind:urgent="item.urgent"
        v-on="$listeners"
      />
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  components: {
    Card
  },
  name: "CardContainer",
  props: ["items"],
  mounted() {
    this.resizeAllGridItems();
  },
  updated() {
    this.resizeAllGridItems();
  },
  methods: {
    resizeGridItem(item) {
      let rowHeight = parseInt(
        window
          .getComputedStyle(document.querySelector(".card-container"))
          .getPropertyValue("grid-auto-rows")
      );
      let rowGap = parseInt(
        window
          .getComputedStyle(document.querySelector(".card-container"))
          .getPropertyValue("grid-row-gap")
      );

      let rowSpan = Math.ceil(
        (item.querySelector(".content").getBoundingClientRect().height +
          rowGap +
          60) /
          (rowHeight + rowGap)
      );
      item.style.gridRowEnd = `span ${rowSpan}`;
    },
    resizeAllGridItems() {
      console.log("resized");
      var allItems = document.querySelectorAll(".card");
      allItems.forEach(item => this.resizeGridItem(item));
    }
  }
};
</script>

<style>
.card-container {
  background-color: #f3f6f7;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-auto-rows: 10px;
  padding: 2em;
  grid-area: cards;
}
.wrapper {
  background-color: #f3f6f7;
  width: 100%;
}
</style>
