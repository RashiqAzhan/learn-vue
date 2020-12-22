<template>
  <div class = "user-profile">
    <div class = "user-profile__user_panel">
      <h1 class = "user-profile__username">0{{ user.username }}</h1>
      <div
          v-if = "user.isAdmin"
          class = "user-profile__admin-badge">
        Admin
      </div>
      <div class = "user_profile__follower-count">
        <strong>Followers: </strong> {{ followers }}
      </div>

      <CreateTwootPanel @add-twoot = "addTwoot"/>
    </div>

    <div class = "user-profile__twoots-wrapper">
      <TwootItem
          v-for = "twoot in user.twoots"
          :key = "twoot.id"
          :twoot = "twoot"
          :username = "user.username"/>
    </div>
  </div>
</template>

<script lang = "ts">
import CreateTwootPanel from "./CreateTwootPanel.vue";
import TwootItem        from "./TwootItem.vue";

export default {
  name      : "UserProfiles",
  components: {TwootItem, CreateTwootPanel},
  data() {
    return {
      followers: 0,
      user     : {
        id       : 1,
        username : "_MichellRomney",
        firstName: "Michell",
        lastName : "Rooney",
        email    : "michellromney@theearthissquare.com",
        isAdmin  : true,
        twoots   : [
          {id: 1, content: "Twoots are awesome."},
          {id: 2, content: "Subscribe to the Earth is square."},
        ],
      },
    };
  },
  methods   : {
    addTwoot(twoot) {
      this.user.twoots.unshift({id: this.user.twoots.length + 1, content: twoot});
    },
  },
};
</script>

<style lang = "scss" scoped>
.user-profile {
  display               : grid;
  grid-template-columns : 1fr 3fr;
  padding               : 50px 5%;
  width                 : 100%;


  .user-profile__user_panel {
    background-color : white;
    border           : 1px solid #dfe3e8;
    border-radius    : 5px;
    display          : flex;
    flex-direction   : column;
    margin-right     : 50px;
    padding          : 20px;

    h1 {
      margin : 0;
    }

    .user-profile__admin-badge {
      background    : rebeccapurple;
      border-radius : 5px;
      color         : white;
      font-weight   : bold;
      margin-right  : auto;
      padding       : 0 10px;
    }

    .user-profile__twoots-wrapper {
      display       : grid;
      grid-gap      : 10px;
      margin-bottom : auto;
    }
  }

  .user-profile__create-twoot {
    display        : flex;
    flex-direction : column;
    padding-top    : 20px;

    &.--exceeded {
      border-color : red;
      color        : red;

      button {
        background-color : red;
        border           : none;
        color            : white;
      }
    }
  }
}

</style>
