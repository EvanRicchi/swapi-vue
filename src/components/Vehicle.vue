<template>
  <div class="container-fluid clearfix">
    <div class="row">
      <div class="col-sm-4" v-for="vehicles in vehicle">
        <div class="card bg-light">
          <div class="card-body">
            <h3 class="card-title">{{vehicles.name}}</h3>
            <p class="card-text">Length : {{vehicles.length}} m</p>
            <p class="card-text">Passenger(s) : {{vehicles.passengers}} passenger(s)</p>
            <p class="card-text">Model : {{vehicles.model}}</p>
            <p class="card-text">Vehicle class : {{vehicles.vehicle_class}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import axios from 'axios'

  export default {
    name: 'Vehicle',

    data () {
      return {
        vehicle: {}
      }
    },
    methods: {
      loadVehicle() {
        axios.get('https://swapi.co/api/vehicles/?format=json')
          .then((response) => {
            this.vehicle = response.data.results;
          });
      }
    },
    mounted() {
      // When the Component is ready fetch the JSON from the Server Backend
      this.loadVehicle();
    },
  }
</script>
