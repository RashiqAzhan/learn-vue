<template>
  <div class = "twoot-item">
    <div class = "user-profile_twoot">
      <div class = "twoot-item__user">@{{ username }}</div>
      <div class = "twoot-item__content">{{ twoot.content }}</div>
    </div>
  </div>
</template>

<script lang = "ts">
export default {
  name   : "TwootItem",
  props  : {
    username: {
      type    : String,
      required: true,
    },
    twoot   : {
      type    : Object,
      required: true,
    },
  },
};
</script>

<style lang = "scss" scoped>
.twoot-item {
  background-color : 5px;
  border           : 1px solid #dfe3e8;
  border-radius    : 5px;
  box-sizing       : border-box;
  cursor           : pointer;
  padding          : 20px;
  transition       : all 0.25s ease;

  &:hover {
    transform : scale(1.1, 1.1);
  }

  .twoot-item__user {
    font-weight : bold;
  }
}

</style>
