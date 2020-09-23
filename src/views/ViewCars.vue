<template>
  <div class="container">
    <div class="columns is-multiline">
      <div class="column" v-if="!(cars.length !== 0)">Neradau Masinu</div>
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
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "ViewCars",
  components: {},
  data() {
    return {
      cars: [],
      carbs: [
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
  methods: {
    carView(cars) {
      console.log(cars);
      if (cars.length === 0) {
        return false;
      } else {
        return cars;
      }
    },
  },
};
</script>

<style scoped>
.cars {
  display: flex;
  flex-wrap: wrap;
}
.car {
  width: 100%;
}
</style>
