<template>
  <div id="app">
    <h1 class="nav-bar">
      Check <span class="nav-bar-highlight">Yo'</span> Self
    </h1>
    <main>
      <Form />
      <CardContainer :items="items" />
    </main>
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

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body,
html {
  height: 100%;
  width: 100%;
}

main {
  display: flex;
}

.nav-bar {
  background: #1f1e3d;
  color: white;
  text-transform: uppercase;
  font-family: "Open Sans", sans-serif;
  font-weight: 800;
  padding: 0.3em;
}

.nav-bar-highlight {
  color: #ffc211;
}
</style>
