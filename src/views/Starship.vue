<template>
  <div>
    <img src="../assets/starship.png" alt="Starship" width="400" />
    <h1>{{ starship.name }}</h1>
    <p>Model: {{ starship.model }}</p>
    <p>Hyperdrive Rating: {{ starship.hyperdrive_rating }}</p>
    <p>Passengers: {{ starship.passengers }}</p>
    <p>Max Atmosphering Speed: {{ starship.max_atmosphering_speed }}</p>
    <p>Manufacturer: {{ starship.manufacturer }}</p>
    <p>Crew: {{ starship.crew }}</p>
    <p>Cargo Capacity: {{ starship.cargo_capacity }}</p>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Starship',
  data() {
    return {
      starship: {},
    }
  },
  created() {
    axios
      .get(`https://swapi.dev/api/starships/${this.$route.params.id}`)
      .then((res) => (this.starship = res.data))
  },
}
</script>
