<template>
  <div class="film">
    <div class="container-fluid clearfix">
      <div class="row">
        <div class="col-sm-4" v-for="films in film">
          <div class="card bg-light">
            <div class="card-body">
              <h3 class="card-title">{{films.title}}</h3>
              <p class="card-text">Director : {{films.director}}</p>
              <p class="card-text">Created : {{films.created}}</p>
              <p class="card-text">Edited : {{films.edited}}</p>
              <p class="card-text">{{films.opening_crawl}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import axios from 'axios'

  export default {
    name: 'Film',

    data () {
      return {
        film: {}
      }
    },
    methods: {
      loadFilm() {
        axios.get('https://swapi.co/api/films/?format=json')
          .then((response) => {
            this.film = response.data.results;
          });
      }
    },
    mounted() {
      // When the Component is ready fetch the JSON from the Server Backend
      this.loadFilm();
    },
  }
</script>
