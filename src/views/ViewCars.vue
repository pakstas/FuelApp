<template>
  <div class="columns is-multiline">
    <div
      class="column is-one-third-desktop is-half-tablet"
      v-if="!(cars.length != 0)"
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
              <p class="title is-4">{{ car.brand }}</p>
              <p class="subtitle is-6">{{ car.model + " " + car.id }}</p>
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
          <div class="content">
            <div class="tags has-addons">
              <span class="tag is-large">Year:</span>
              <span class="tag is-large is-dark">{{ car.year }}</span>
            </div>
          </div>
          <div class="content">asdasd</div>
        </div>

        <footer class="card-footer">
          <a href="#" class="card-footer-item">Edit</a>
          <a href="#" class="card-footer-item">Delete</a>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "ViewCars",
  components: {},
  data() {
    return {
      carbs: [],
      cars: [
        {
          brand: "BMW",
          model: "X6",
          year: 1999,
          id: 1,
          fuel: 5,
        },
        {
          brand: "BMW",
          model: "X6",
          year: 1999,
          id: 2,
          fuel: 5,
        },
        {
          brand: "BMW",
          model: "X6",
          year: 1999,
          id: 3,
          fuel: 5,
        },
        {
          brand: "BMW",
          model: "X6",
          year: 1999,
          id: 4,
          fuel: 5,
        },
      ],
    };
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
</style>
