<template>
  <div class="twoot-item">
    <div class="user-profile_twoot">
      <div class="twoot-item__user">@{{ username }}</div>
      <div class="twoot-item__content">{{ twoot.content }}</div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name : "TwootItem",
  props: {
    username: {
      type    : String,
      required: true,
    },
    twoot   : {
      type    : Object,
      required: true,
    },

  }
}
</script>

<style scoped>
.twoot-item {
  padding: 20px;
  background-color: 5px;
  border-radius: 5px;
  border: 1px solid #DFE3E8;
  box-sizing: border-box;
  cursor: pointer;
  transition: all 0.25s ease;
}

.twoot-item:hover {
  transform: scale(1.1, 1.1);
}

.twoot-item__user {
  font-weight: bold;
}
</style>