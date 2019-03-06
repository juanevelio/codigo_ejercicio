<template>
  <div id="app">
    <div class="hero is-white is-gradient is-bold">
      <div class="hero-body">
        <h1 class="title">
          <span class="has-text-success"> R&M </span>
          <span class="subtitle"> personajes de la serie </span>
        </h1>
        <button class="button is-success is-rounded" v-on:click="fetch">
          Consultar
        </button>
      </div>
    </div>

    <div class="container">
      <div
        v-for="character in characters"
        v-bind:key="character.id"
        class="columns is-desktop is-mobile is-table is-multiline-is-centered"
      >
        <div class="column is-8-mobile is-4-desktop is-8-tablet">
          <div class="card ">
            <div class="card-header">
              <div class="card-content">
                {{ character.name }}
                <img v-bind:src="character.image" alt="avatar" />
                <button class="button is-success is-rounded is-small">
                  ver mas..
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// aqui importamos nuestras librerias
import axios from "axios";

export default {
  name: "App",
  data: function() {
    return {
      characters: []
    };
  },
  methods: {
    fetch() {
      let results = axios
        .get(" https://rickandmortyapi.com/api/character/")
        .then(res => {
          this.characters = res.data.results;
        })
        .catch(err => {
          console.log(err);
        });
    },
    image() {
      return this.character.image;
    }
  }
};
</script>
