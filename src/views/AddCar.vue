<template>
  <div class="add-car">
    <form>
      <div class="field">
        <label class="label">Car brand</label>
        <div class="control">
          <input class="input" type="text" placeholder="e.g. Audi" required />
        </div>
      </div>
      <div class="field">
        <label class="label">Car model</label>
        <div class="control">
          <input class="input" type="text" placeholder="e.g. A6" required />
        </div>
      </div>
      <div class="field">
        <label class="label">Car year</label>
        <div class="control">
          <input
            class="input"
            type="number"
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
            <select v-model="fuelType">
              <option value="diesel">Diesel</option>
              <option value="petrol" selected>Petrol</option>
            </select>
          </div>
        </div>
      </div>

      <div class="field">
        <label class="label">Car model</label>
        <div class="control">
          <input
            class="input"
            type="url"
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
export default {
  name: "AddCar",
  data() {
    return {
      fuelType: "petrol",
    };
  },
};
</script>

<style scoped>
.add-car {
  margin: 0 auto;
}
</style>
