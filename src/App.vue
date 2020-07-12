<template>
  <div id="app">
    <Nav @search-input="searchInputHandler" />
    <Form
      v-on:add="handleNewList"
      @filter-urgent="filterUrgent"
      :filter="filter"
    />
    <CardContainer
      :items="items"
      :filteredItems="filteredItems"
      @toggle-done="toggleDone"
      @toggle-urgent="toggleUrgent"
      @delete-card="deleteCard"
    />
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
      this.items = this.items.filter(task => task.id !== id);
    },
    filterUrgent: function() {
      this.filter = !this.filter;
    },
    searchInputHandler: function(input) {
      this.searchInput = input;
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
          urgent: true
        }
      ],
      filter: false,
      searchInput: ""
    };
  },
  computed: {
    filteredItems() {
      let filteredList = this.items.slice();
      if (this.searchInput) {
        filteredList = filteredList.filter(item => {
          let match =
            item.title.includes(this.searchInput) ||
            item.tasks.some(task => {
              return task.description.includes(this.searchInput);
            });
          return match;
        });
      }
      if (this.filter) {
        return filteredList.filter(item => item.urgent);
      } else {
        return filteredList;
      }
    }
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

#app,
body,
html {
  height: 100%;
  width: 100%;
}

#app {
  display: grid;
  font-family: "Open Sans", sans-serif;
  grid-template-areas:
    "nav nav"
    "dashboard cards";
  grid-template-columns: 23em 1fr;
  grid-template-rows: 75px 1fr;
}
</style>
