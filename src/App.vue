<template>
  <div id="app">
    <div id="nav">
      <router-link class="button is-dark" to="/">Home</router-link>
      <router-link class="button is-dark" to="/about">About</router-link>
      <router-link class="button is-dark" to="/login">Login</router-link>
      <router-link class="button is-dark" to="/register">Register</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
body,
html {
  height: 100%;
}
body {
  background-image: url("./assets/img/bg_car.jpg");
  background-position: center center;
  background-attachment: fixed;
  background-size: cover;
}
</style>
