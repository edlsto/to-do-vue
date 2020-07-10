<template>
  <div class="card">
    <div class="content">
      <div class="title">{{ title }}</div>
      <div class="items-container">
        <div
          class="item-container"
          v-for="(task, index) in tasks"
          v-bind:key="index"
        >
          <img
            :src="!completed ? completedImg : notCompletedImg"
            class="checkbox"
            v-on:click="toggleDone"
          />
          <div class="description">
            {{ task.description }}
          </div>
        </div>
      </div>
    </div>
    <div class="buttons-row">
      <div class="urgent-container">
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
  props: ["title", "tasks"],
  data() {
    return {
      completedImg: completed,
      notCompletedImg: notCompleted
    };
  },
  methods: {
    toggleDone: function() {
      this.completed = !this.completed;
    }
  }
};
</script>

<style>
.card {
  border: 1px solid #c7d3d8;
  padding: 0.2em;
  background-color: #fafdff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.title {
  font-weight: bold;
  padding: 0.3em 1em;
}

.checkbox {
  height: 1em;
  margin-right: 0.5em;
  margin-top: 0.25em;
  cursor: pointer;
}

.item-container {
  display: flex;

  padding: 0.7em 1em;
}

.icon {
  height: 1.6em;
}

.buttons-row {
  display: flex;
  justify-content: space-between;
  margin: 0.5em 1em 0.2em 1em;
}

.delete-container,
.urgent-container {
  text-align: center;
  text-transform: uppercase;
  cursor: pointer;
}

.icon-text {
  font-size: 0.7em;
}
.items-container {
  border-top: 1px solid #c7d3d8;
  border-bottom: 1px solid #c7d3d8;
}
</style>
