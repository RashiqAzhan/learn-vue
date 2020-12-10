<template>
  <div class = "user-profile">
    <div class = "user-profile__user_panel">
      <h1 class = "user-profile__username">0{{ user.username }}</h1>
      <div v-if = "user.isAdmin"
           class = "user-profile__admin-badge">
        Admin
      </div>
      <div class = "user_profile__follower-count">
        <strong>Followers: </strong> {{ followers }}
      </div>
      <form class = "user-profile__create-twoot"
            @submit.prevent = "createNewTwoot">
        <label for = "newTwoot"><strong>New Twoot</strong></label>
        <textarea id = "newTwoot" v-model = "newTwootContent" name = ""
                  rows = "4"></textarea>

        <div class = "user-profile__create-twoot-type">
          <label for = "newTwootType"><strong>Type: </strong></label>
          <select id = "newTwootType" v-model = "selectedTwootType"
                  name = "">
            <option
                v-for = "(option, index) in twootTypes"
                :key = "index"
                :value = "option.value">
              {{ option.name }}
            </option>
          </select>
        </div>
        <button>Twoot</button>
      </form>
    </div>
    <div class = "user-profile__twoots-wrapper">
      <TwootItem v-for = "twoot in user.twoots"
                 :key = "twoot.id"
                 :twoot = "twoot"
                 :username = "user.username"
                 @favorite = "toggleFavourite"/>
    </div>
  </div>
</template>

<script lang = "ts">
import TwootItem from "./TwootItem.vue";

export default {
  name      : "UserProfiles",
  components: {TwootItem},
  data() {
    return {
      followers        : 0,
      user             : {
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
      twootTypes       : [
        {value: "draft", name: "Draft"},
        {value: "instant", name: "Instant Twoot"},
      ],
      newTwootContent  : "",
      selectedTwootType: "instant",

    }
  },
  watch     : {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`)
      }
    },
  },
  computed  : {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    },
  },
  methods   : {
    followUser() {
      ++this.followers
    },
    toggleFavourite(id) {
      console.log(`Favourited Tweet #${id}`);
    },
    createNewTwoot() {
      if (this.newTwootContent && this.selectedTwootType !== "draft") {
        this.user.twoots.unshift({
          id: this.user.twoots.length + 1, content: this.newTwootContent,
        })
        this.newTwootContent = "";
      }
    },
  },
  mounted() {
    this.followUser()
  },
}
</script>

<style scoped>
.user-profile {
  display               : grid;
  grid-template-columns : 1fr 3fr;
  padding               : 50px 5%;
  width                 : 100%;
}

.user-profile__user_panel {
  background-color : white;
  border           : 1px solid #dfe3e8;
  border-radius    : 5px;
  display          : flex;
  flex-direction   : column;
  margin-right     : 50px;
  padding          : 20px;
}

h1 {
  margin : 0;
}

.user-profile__admin-badge {
  background    : rebeccapurple;
  border-radius : 5px;
  color         : white;
  font-weight   : bold
  margin-right  : auto;
  padding       : 0 10px;
}

.user-profile__twoots-wrapper {
  display       : grid;
  grid-gap      : 10px;
  margin-bottom : auto;
}

.user-profile__create-twoot {
  display        : flex;
  flex-direction : column;
  padding-top    : 20px;
}
</style>
