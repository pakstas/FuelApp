<template>
  <div id="app">
    <div class="wrapper"><Header /> <router-view /></div>
  </div>
</template>

<script>
import Header from "./components/Header";

export default {
  components: {
    Header,
  },
};
</script>

<style>
body {
  background-image: url("./assets/img/bg_car.jpg");
  background-position: center center;
  background-attachment: fixed;
  background-size: cover;
}
</style>
<style scoped>
#app {
  min-height: 100vh;
}
.wrapper {
  width: 768px;
  margin: 0 auto;
}
</style>
