<template>
  <div id = "app">
    <UserProfiles/>
  </div>
</template>

<script lang = "ts">

import UserProfiles from "./components/UserProfiles.vue";

export default {
  name      : "app",
  components: {UserProfiles},
};
</script>

<style lang = "scss">
#app {
  background-color        : #f3f5fa;
  color                   : #2c3e50;
  font-family             : Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing  : antialiased;
  min-height              : 100 hv;
  -moz-osx-font-smoothing : grayscale;
}
</style>
