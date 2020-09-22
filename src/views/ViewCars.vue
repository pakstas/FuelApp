<template>
  <div class="container">
    <div class="cars">
      <div class="car" v-for="car in cars" :key="car.id">
        <div class="card">
          <div class="card-content car-title">
            <div class="media">
              <div class="media-content">
                <p class="title is-4">{{ car.brand}}</p>
                <p class="subtitle is-6">{{ car.model + " " + car.id}}</p>
              </div>
            </div>
          </div>

          <div class="card-image">
            <figure class="image is-4by3">
              <img src="https://bulma.io/images/placeholders/1280x960.png" alt="Placeholder image" />
            </figure>
          </div>

          <div class="card-content">
            <div class="content">
              Lorem, ipsum dolor sit amet consectetur adipisicing elit. Cum, amet similique? Modi magnam deleniti architecto est inventore iste, non eum totam impedit quia amet. Harum animi architecto assumenda vero reiciendis.
              <a
                href="#"
              >#css</a>
              <a href="#">#responsive</a>
            </div>
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
      ],
    };
  },
};
</script>

<style scoped>
.cars {
  display: flex;
  flex-wrap: wrap;
}
</style>
