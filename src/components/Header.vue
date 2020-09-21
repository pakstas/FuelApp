<template>
  <header>
    <div class="container">
      <img src="../assets/img/Fuel_Logo.png" alt="Company logo" />
      <nav>
        <span v-if="userAuth">
          <a v-on:click="signOut()">Sign Out {{ "(" + email + ")" }}</a>
        </span>
        <span v-else>
          <router-link to="/register">Register</router-link>
          <router-link to="/login">Login</router-link>
        </span>
      </nav>
    </div>
  </header>
</template>

<script>
import firebase from "firebase/app";
import "firebase/auth";
export default {
  name: "Header",
  data() {
    return {
      userAuth: "",
      email: "",
    };
  },
  methods: {
    signOut() {
      firebase.auth().signOut();
      this.$router.push("/login");
      this.userAuth = false;
    },
  },
  beforeMount() {
    firebase.auth().onAuthStateChanged((user) => {
      if (user) {
        this.userAuth = true;
        this.email = firebase.auth().currentUser.email;
      } else {
        this.userAuth = false;
      }
    });
  },
};
</script>

<style scoped>
div.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5px;
}

.container {
  width: 768px;
  margin: 0 auto;
  background: rgba(255, 255, 255, 0.55);
  border-radius: 0px 0px 5px 5px;
}
.container > img {
  height: 40px;
}

a {
  text-decoration: none;
  color: rgb(0, 0, 0);
  margin-right: 5px;
}
</style>
