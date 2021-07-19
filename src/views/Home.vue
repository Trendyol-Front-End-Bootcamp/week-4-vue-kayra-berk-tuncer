<template>
  <div class="home">
    <HelloWorld />
    <div class="starships">
      <div v-for="ship in starships" :key="ship.id">
        <router-link :to="'/' + ship.url.split('/').reverse()[1]">
          <div class="shipCard">
            <img src="../assets/starship.png" width="100" />
            <div class="shipCard-info">
              <h3>{{ ship.name }}</h3>
              <p>{{ ship.model }}</p>
              <p>{{ ship.hyperdrive_rating }}</p>
            </div>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import HelloWorld from '../components/HelloWorld'

export default {
  name: 'Home',
  components: {
    HelloWorld,
  },
  data() {
    return {
      search: '',
      starships: [],
    }
  },
  methods: {
    handleSearch: function() {
      axios
        .get(`https://swapi.dev/api/starships?search=${this.search}`)
        .then((res) => {
          this.starships = [...res.data.results]
        })
    },
  },
  mounted() {
    axios.get(`https://swapi.dev/api/starships`).then((res) => {
      this.starships = [...res.data.results]
    })
  },
}
</script>

<style scoped>
.home {
  display: flex;
  flex-direction: column;
}
</style>
