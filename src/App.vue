<template>
  <div id="app">
    <Nav />
    <main>
      <Form v-on:add="handleNewList" />
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
    }
  },
  data() {
    return {
      items: [
        {
          title: "go to store",
          tasks:
            "get some stuff get some stuff get some stuff get some stuff get some stuff get some stuff get some stuff"
        },
        { title: "go somewhere else", tasks: "get some more stuff" },
        { title: "go somewhere else", tasks: "get some more stuff" },
        { title: "go somewhere else", tasks: "get some more stuff" },
        { title: "go somewhere else", tasks: "go somewhere else" },
        { title: "go somewhere else", tasks: "get some more stuff" }
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
