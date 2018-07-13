<template>
  <div class="container-fluid clearfix">
    <div class="row">
      <div class="col-sm-4" v-for="planets in planet">
        <div class="card bg-light">
          <div class="card-body">
            <h3 class="card-title">{{planets.name}}</h3>
            <p class="card-text">Climate : {{planets.climate}}</p>
            <p class="card-text">Created : {{planets.created}}</p>
            <p class="card-text">Gravity : {{planets.gravity}}</p>
            <p class="card-text">Population : {{planets.population}} person(s)</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import axios from 'axios'

  export default {
    name: 'Planet',

    data () {
      return {
        planet: {}
      }
    },
    methods: {
      loadPlanet() {
        axios.get('https://swapi.co/api/planets/?format=json')
          .then((response) => {
            this.planet = response.data.results;
          });
      }
    },
    mounted() {
      // When the Component is ready fetch the JSON from the Server Backend
      this.loadPlanet();
    },
  }
</script>
