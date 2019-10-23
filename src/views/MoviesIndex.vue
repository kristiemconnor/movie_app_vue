<template>
  <div class="index">
    <br />
    <div class="container-fluid pt80 pb80">
      <datalist id="names">
        <option v-for="movie in movies">{{ movie.title }}</option>
      </datalist>
      <div id="fh5co-projects-feed" class="fh5co-projects-feed clearfix masonry">
        Search by Title:
        <input v-model="titleFilter" list="names" />
        <br />
        <br />
        <div>
          <button v-on:click="sortByAttribute('director')">Sort by Director</button>
          <br />
          <button v-on:click="sortByAttribute('year')">Sort by Year</button>
          <br />
        </div>
        <div
          v-for="movie in orderBy(filterBy(movies, titleFilter, 'title'), sortAttribute)"
          class="fh5co-project masonry-brick"
        >
          <router-link
            :to="{
              name: 'show',
              params: {
                id: movie.id
              }
            }"
          >
            <h2>{{ movie.title }}</h2>
          </router-link>
        </div>
      </div>
      <!--END .fh5co-projects-feed-->
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
import Vue2Filters from "vue2-filters";
export default {
  mixins: [Vue2Filters.mixin],
  data: function() {
    return {
      movies: [],
      currentMovie: {},
      titleFilter: "",
      sortAttribute: "title"
    };
  },
  created: function() {
    axios.get("/api/movies").then(response => {
      console.log(response.data);
      this.movies = response.data;
    });
  },
  methods: {
    sortByAttribute: function(attribute) {
      this.sortAttribute = attribute;
    }
  }
};
</script>
