<template>
  <div id="app">
    <Nav />
    <main>
      <Form v-on:add="handleNewList" v-on:delete-all="deleteAll" />
      <CardContainer :items="items" />
    </main>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import CardContainer from "./components/cardContainer.vue";
import Nav from "./components/Nav.vue";
export default {
  components: {
    Form,
    CardContainer,
    Nav
  },
  name: "app",
  methods: {
    handleNewList: function(list) {
      this.items.push(list);
    },
    deleteAll: function() {
      this.items = [];
    }
  },
  data() {
    return {
      items: [
        {
          title: "go to store",
          tasks: [
            { description: "get some stuff", completed: false },
            { description: "hello", completed: false },
            { description: "hi", completed: false }
          ]
        },

        {
          title: "go somewhere else",
          tasks: [
            { description: "get some stuff", completed: false },
            { description: "hello", completed: false },
            { description: "hi", completed: false }
          ]
        }
      ]
    };
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Open Sans", sans-serif;
}

body,
html {
  height: 100%;
  width: 100%;
}

main {
  display: flex;
}
</style>
