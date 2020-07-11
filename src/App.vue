<template>
  <div id="app">
    <Nav />
    <main>
      <Form v-on:add="handleNewList" />
      <CardContainer
        :items="items"
        @toggle-done="toggleDone"
        @toggle-urgent="toggleUrgent"
        @delete-card="deleteCard"
      />
    </main>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import CardContainer from "./components/CardContainer.vue";
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
    toggleDone: function(id) {
      const targetItem = this.items.find(item =>
        item.tasks.some(task => task.id === id)
      );
      const targetTask = targetItem.tasks.find(task => task.id === id);
      targetTask.completed = !targetTask.completed;
    },
    toggleUrgent: function(id) {
      const targetItem = this.items.find(item => item.id === id);
      targetItem.urgent = !targetItem.urgent;
    },
    deleteCard: function(id) {
      console.log(id);
      this.items = this.items.filter(task => task.id !== id);
    }
  },
  data() {
    return {
      items: [
        {
          title: "go to store",
          tasks: [
            { description: "get some stuff", completed: false, id: 1 },
            { description: "hello", completed: false, id: 2 },
            { description: "hi", completed: false, id: 3 }
          ],
          id: 1,
          urgent: false
        },

        {
          title: "go somewhere else",
          tasks: [
            { description: "get some stuff", completed: false, id: 4 },
            { description: "hello", completed: false, id: 5 },
            { description: "hi", completed: false, id: 6 }
          ],
          id: 2,
          urgent: false
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
