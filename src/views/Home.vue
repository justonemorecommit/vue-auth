<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <div>
      <button type="button" @click="signIn" v-if="!currentUser">
        Sign In with Google
      </button>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

import firebase from "firebase";

export default {
  name: "home",
  data() {
    return {
      currentUser: null
    };
  },
  methods: {
    signIn() {
      const provider = new firebase.auth.GoogleAuthProvider();

      firebase
        .auth()
        .signInWithPopup(provider)
        .then(() => {
          // This gives you a Google Access Token.
          // const token = result.credential.accessToken;
          // // The signed-in user info.
          // const user = result.user;
          this.$router.go("secret");
        });
    }
  },
  mounted() {
    this.currentUser = firebase.auth().currentUser;
  }
  // components: {
  //   HelloWorld
  // }
};
</script>
