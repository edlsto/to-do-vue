<template>
  <div class="form">
    <div class="form-item">
      <label class="form-label">Task Title</label>
      <input class="form-input" type="text" />
    </div>
    <ul class="draft-task-list">
      <div
        class="draft-task-container"
        v-for="(task, index) in tasks"
        v-bind:key="index"
      >
        <img
          src="../assets/delete.svg"
          alt="Delete task"
          class="draft-task-delete-icon"
        />
        <li class="draft-task">
          {{ task }}
        </li>
      </div>
    </ul>
    <div class="form-item">
      <label class="form-label">Task Item</label>
      <div class="task-item-container">
        <input class="form-input" v-model="newTask" type="text" />
        <button class="add-task-btn" v-on:click="tasks.push(newTask)"></button>
      </div>
    </div>
    <button class="form-btn">Make Task List</button>
    <button class="form-btn">Clear All</button>
    <div class="line"></div>
    <button class="form-btn">Filter By Urgency</button>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      title: "",
      tasks: [],
      newTask: ""
    };
  }
};
</script>

<style>
.form {
  background: #587a8a;
  flex: 0 1 20%;
  height: 100vh;
  display: block;
  padding: 2em;
}
.form-item {
  margin-bottom: 1em;
  justify-content: space-between;
}
.form-btn {
  display: block;
  width: 100%;
  padding: 0.5em;
  background-color: #1f1f3d;
  color: white;
  font-weight: bold;
  font-size: 18px;
  outline: none;
  border: none;
  cursor: pointer;
}

.form-btn:first-of-type {
  margin-bottom: 1em;
}
.form-input {
  display: block;
  width: 100%;
  outline: none;
  height: 3em;
  padding: 0.3em;
}
.form-label {
  color: #c8d3d8;
}
.line {
  height: 1px;
  background-color: #1f1f3d;
  margin: 1em 0;
}
.task-item-container {
  display: flex;
}
.add-task-btn {
  width: 3.5em;
  background: #1f1f3d;
  outline: none;
  border: none;
  margin-left: 0.2em;
}
.draft-task {
  list-style: none;
  color: #fff;
}
.draft-task-delete-icon {
  height: 1em;
  margin-right: 0.3em;
}
.draft-task-container {
  display: flex;
  align-items: center;
}
.draft-task-list {
  margin-bottom: 1em;
}
</style>
