<template>
  <header>
    <div class="wrapper">
      <div class="nav">
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
      <div class="page-title" v-if="userAuth">
        <h1 class="title">{{ this.$route.name }}</h1>
      </div>
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
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5px;
  /* background: rgba(255, 255, 255, 0.55); */
  background: rgb(147, 224, 243);
  border-radius: 0px 0px 5px 5px;
}

.nav img {
  height: 40px;
}

.nav a {
  text-decoration: none;
  color: rgb(0, 0, 0);
  margin-right: 5px;
  margin-left: 10px;
}
.nav a:hover {
  text-decoration: underline;
  box-shadow: 1px 1px 0px 0px rgba(255, 255, 255, 0.55);
}

.nav a:last-child {
  margin-right: 0px;
}

nav {
  display: flex;
  justify-content: space-between;
}

.wrapper .page-title {
  height: 200px;
  padding: 5px;
  display: flex;
  align-items: center;
  background: rgba(255, 255, 255, 0.55);
}
</style>
