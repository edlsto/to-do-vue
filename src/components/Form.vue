<template>
  <div class="form">
    <div class="form-item">
      <label class="form-label">Task Title</label> <input class="form-input" />
    </div>
    <div class="form-item">
      <label class="form-label">Task Item</label> <input class="form-input" />
    </div>
    <button class="form-btn">Make Task List</button>
    <button class="form-btn">Clear All</button>
  </div>
</template>

<script>
export default {
  name: "Form"
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
</style>
