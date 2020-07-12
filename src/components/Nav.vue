<template>
  <h1 class="nav-bar">Check <span class="nav-bar-highlight">Yo'</span> Self</h1>
</template>

<script>
export default {
  name: "Nav"
};
</script>

<style>
.nav-bar {
  background: #1f1e3d;
  color: white;
  text-transform: uppercase;
  font-family: "Open Sans", sans-serif;
  font-weight: 800;
  padding: 0.3em;
  grid-area: nav;
  font-size: 2.5em;
}

.nav-bar-highlight {
  color: #ffc211;
}
</style>
