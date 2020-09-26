<template>
  <div class="add-car">
    <form v-on:submit.prevent="addCar()">
      <div class="field">
        <label class="label">Car brand</label>
        <div class="control">
          <input
            class="input"
            type="text"
            v-model="brand"
            placeholder="e.g. Audi"
            required
          />
        </div>
      </div>
      <div class="field">
        <label class="label">Car model</label>
        <div class="control">
          <input
            class="input"
            type="text"
            v-model="model"
            placeholder="e.g. A6"
            required
          />
        </div>
      </div>
      <div class="field">
        <label class="label">Car year</label>
        <div class="control">
          <input
            class="input"
            type="number"
            v-model="year"
            min="1900"
            max="2050"
            placeholder="e.g. 1997"
            required
          />
        </div>
      </div>

      <div class="field">
        <label class="label">Fuel type</label>
        <div class="control">
          <div class="select">
            <select v-model="fueltype">
              <option value="diesel">Diesel</option>
              <option value="petrol" selected>Petrol</option>
            </select>
          </div>
        </div>
      </div>

      <div class="field">
        <label class="label">Car image</label>
        <div class="control">
          <input
            class="input"
            type="url"
            v-model="image"
            placeholder="e.g. http://www.google.lt/images/audi.jpg"
            required
          />
        </div>
      </div>

      <div class="control">
        <button class="button is-dark" type="submit">Add this!</button>
      </div>
    </form>
  </div>
</template>

<script>
import firebase from "firebase/app";
import "firebase/auth";
import "firebase/firestore";

export default {
  name: "AddCar",
  data() {
    return {
      fueltype: "petrol",
      brand: "",
      model: "",
      image: "",
      year: "",
    };
  },
  methods: {
    addCar() {
      firebase
        .firestore()
        .collection("users")
        .doc(firebase.auth().currentUser.uid)
        .collection("cars")
        .add({
          brand: this.brand,
          model: this.model,
          year: Number(this.year),
          fueltype: this.fueltype,
          image: this.image,
        })
        .then(() => alert("Car Added"))
        .catch((error) => alert(error));
    },
  },
};
</script>

<style scoped></style>
