<template>
  <div class="login">
    <div class="title">
      <h2>Login</h2>
    </div>
    <div class="form">
      <Notification
        v-on:close="error = false"
        v-if="error"
        :type="errorType"
        :message="errorMessage"
      />
      <form v-on:submit.prevent="login">
        <div class="field">
          <label class="label">Email</label>
          <div class="control">
            <input
              class="input"
              type="email"
              v-model="email"
              placeholder="e.g. alexsmith@gmail.com"
            />
          </div>
        </div>

        <div class="field">
          <label class="label">Password</label>
          <div class="control">
            <input
              class="input"
              v-model="password"
              type="password"
              placeholder="Password"
            />
          </div>
        </div>

        <div class="field">
          <div class="control">
            <button
              class="button is-dark"
              :class="loading && 'is-loading'"
              type="submit"
            >
              Login
            </button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import firebase from "firebase/app";
import "firebase/auth";
import Notification from "../components/Notification";
export default {
  name: "Login",
  components: { Notification },
  data() {
    return {
      email: "",
      password: "",
      error: false,
      errorMessage: "",
      loading: false,
      errorType: "",
    };
  },
  methods: {
    login() {
      this.loading = true;
      firebase
        .auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then(
          () => this.$router.push("/"),
          (error) => {
            this.error = true;
            this.errorMessage = error.message;
            this.errorType = "is-danger";
            this.loading = false;
          }
        );
    },
  },
};
</script>

<style scoped>
.login {
  width: 350px;
  margin: 20% auto;
  background: rgba(255, 255, 255, 0.55);
  border-radius: 0px 0px 5px 5px;
}

.title {
  background: black;
  color: white;
  padding: 10px 20px 10px 20px;
  margin-bottom: 5px;
  border-radius: 5px 5px 0px 0px;
}

.form {
  padding: 5px 20px 20px 20px;
}
</style>
