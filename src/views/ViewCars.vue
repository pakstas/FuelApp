<template>
  <div class="columns is-multiline">
    <div
      class="column is-one-third-desktop is-half-tablet"
      v-if="!(cars.length !== 0)"
    >
      <span>You haven't added any cars, please start by adding one.</span>
      <router-link to="/addcar"
        ><button class="button is-dark">Add Car</button></router-link
      >
    </div>
    <div
      class="column is-one-third-desktop is-half-tablet"
      v-for="car in cars"
      :key="car.id"
    >
      <div class="card">
        <div class="card-content car-title">
          <div class="media">
            <div class="media-content">
              <p class="title is-4">{{ car.brand + " " + car.model }}</p>
              <div class="tags are-large">
                <span class="tag">{{ car.id }}</span>
                <span class="tag">{{ car.id }}</span>
              </div>
            </div>
          </div>
        </div>

        <div class="card-image">
          <figure class="image is-4by3">
            <img
              src="https://bulma.io/images/placeholders/1280x960.png"
              alt="Placeholder image"
            />
          </figure>
        </div>

        <div class="card-content">
          <div class="content">Fuel average: 8.7 l/100km</div>
          <div class="content">Fuel average (last): 7.4 l/100km</div>
          <div class="content">Last fuel price: 1.23 eur/l</div>
          <div class="content">Last filling date: 2020-09-23</div>
        </div>

        <footer class="card-footer">
          <a href="#" class="card-footer-item">View Fuel</a>
          <a href="#" class="card-footer-item">Edit Car</a>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import firebase from "firebase/app";
import "firebase/auth";
import "firebase/firestore";

export default {
  name: "ViewCars",
  components: {},
  data() {
    return {
      cars: [],
    };
  },
  beforeMount() {
    firebase
      .firestore()
      .collection("users")
      .doc(firebase.auth().currentUser.uid);
  },
};
</script>

<style scoped>
.columns {
  justify-content: space-evenly;
  margin: 0px;
}

div > .card {
  border-radius: 10px;
}

.columns:last-child {
  margin-bottom: 0px;
}

.card-content > div.content {
  margin-bottom: 0px;
}
</style>
