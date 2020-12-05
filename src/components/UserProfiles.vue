<template>
  <div class="user-profile">
    <div class="user-profile__user_panel">
      <h1 class="user-profile__username">0{{ user.username }}</h1>
      <div class="user-profile__admin-badge" v-if="user.isAdmin">
        Admin
      </div>
      <div class="user_profile__follower-count">
        <strong>Followers: </strong> {{ followers }}
      </div>
    </div>
    <div class="user-profile__twoots-wrapper">
      <TwootItem v-for="twoot in user.twoots" :key="twoot.id" :username="user.username" :twoot="twoot"
                 @favorite="toggleFavourite"/>
    </div>
  </div>
</template>

<script lang="ts">
import TwootItem from "./TwootItem.vue";

export default {
  name      : "UserProfiles",
  components: {TwootItem},
  data() {
    return {
      followers: 0,
      user     : {
        id       : 1,
        username : '_MichellRomney',
        firstName: "Michell",
        lastName : 'Rooney',
        email    : 'michellromney@theearthissquare.com',
        isAdmin  : true,
        twoots   : [
          {id: 1, content: "Twoots are awesome."},
          {id: 2, content: "Subscribe to the Earth is square."},
        ],
      },
    }
  },
  watch     : {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`)
      }
    }
  },
  computed  : {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods   : {
    followUser() {
      ++this.followers
    },
    toggleFavourite(id) {
      console.log(`Favourited Tweet #${id}`);
    }
  },
  mounted() {
    this.followUser()
  },
}
</script>

<style scoped>
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile__user_panel {
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #DFE3E8;
}

h1 {
  margin: 0;
}

.user-profile__admin-badge {
  background: rebeccapurple;
  color: white;
  border-radius: 5px;
  margin-right: auto;
  padding: 0 10px;
  font-weight: bold
}

.user-profile__twoots-wrapper {
  display: grid;
  grid-gap: 10px;
  margin-bottom: auto;
}
</style>