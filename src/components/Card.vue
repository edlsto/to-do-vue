<template>
  <div :class="!urgent ? 'card' : 'card card-urgent'" :id="id">
    <div class="content">
      <div class="title">{{ title }}</div>
      <div class="items-container">
        <div
          class="item-container"
          v-for="(task, index) in tasks"
          v-bind:key="index"
          :id="task.id"
        >
          <img
            :src="!task.completed ? completedImg : notCompletedImg"
            class="checkbox"
            v-on:click="toggleDone"
          />
          <div
            :class="!task.completed ? 'description' : 'description-completed'"
          >
            {{ task.description }}
          </div>
        </div>
      </div>
    </div>
    <div class="buttons-row">
      <div v-on:click="toggleUrgent" class="urgent-container">
        <img class="icon" src="../assets/urgent.svg" alt="Urgent" />
        <p class="icon-text">Urgent</p>
      </div>
      <div class="delete-container">
        <img class="icon" src="../assets/delete.svg" alt="Delete" />
        <p class="icon-text">Delete</p>
      </div>
    </div>
  </div>
</template>

<script>
import notCompleted from "../assets/checkbox-active.svg";
import completed from "../assets/checkbox.svg";
export default {
  name: "Card",
  props: ["title", "tasks", "id", "urgent"],
  data() {
    return {
      completedImg: completed,
      notCompletedImg: notCompleted
    };
  },
  methods: {
    toggleDone: function(event) {
      const target = this.tasks.find(
        task => task.id === parseInt(event.target.closest(".item-container").id)
      );
      target.completed = !target.completed;
    },
    toggleUrgent: function(event) {
      console.log(event.target.closest(".card").id);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.card {
  border: 1px solid #c7d3d8;
  background-color: #fafdff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.card-urgent {
  background-color: #ffe89d;
  border: 1px solid #ffc30c;
}

.title {
  font-weight: bold;
  padding: 0.3em 1em;
  border-bottom: 1px solid #c7d3d8;
}

.checkbox {
  height: 1em;
  margin-right: 0.5em;
  margin-top: 0.25em;
  cursor: pointer;
}

.item-container {
  display: flex;
  padding: 0.7em;
}

.icon {
  height: 1.7em;
}

.buttons-row {
  display: flex;
  justify-content: space-between;
  border-top: 1px solid #c7d3d8;
  padding: 0.5em;
}

.delete-container,
.urgent-container {
  text-align: center;
  text-transform: uppercase;
  cursor: pointer;
}

.icon-text {
  font-size: 0.7em;
  color: #356c77;
}

.description-completed {
  font-style: italic;
  color: #356c77;
}
.items-container {
  padding: 0.5em 0;
}
</style>
