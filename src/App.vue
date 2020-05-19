<template>
  <div id="app">
    <h1>Remember this!</h1>
    <Form />
    <CardContainer :items="items" />
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import CardContainer from "./components/cardContainer.vue";
export default {
  components: {
    Form,
    CardContainer
  },
  name: "app",
  data() {
    return {
      items: [
        { title: "go to store", description: "get some stuff" },
        { title: "go somewhere else", description: "get some more stuff" }
      ]
    };
  }
};
</script>

<style></style>
