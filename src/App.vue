<template>
  <div id="app">
    <UserProfiles/>
  </div>
</template>

<script lang="ts">

import UserProfiles from "./components/UserProfiles.vue";

export default {
  name      : 'app',
  components: {UserProfiles}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100 hv;
  background-color: #F3F5FA
}
</style>
