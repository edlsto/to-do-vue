<template>
  <div class="form">
    <div class="form-item"><label>Task Title</label> <input /></div>
    <div class="form-item"><label>Task Item</label> <input /></div>
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
  display: flex;
  justify-content: space-between;
}
</style>
