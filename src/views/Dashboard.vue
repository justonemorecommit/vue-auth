<template>
  <div class="about">
    <h1>This is the dashboard page</h1>
    <button type="button" @click="signOut">Sign out</button>
  </div>
</template>

<script>
import firebase from "firebase";

export default {
  name: "dashboard",
  methods: {
    signOut() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.go("home");
        });
    }
  }
};
</script>
