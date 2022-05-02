<template>
  <div>
    <h1>Upcoming Movies</h1>
    <div v-for="movie in movies" :key="movie.id">
      <router-link :to="`/movie/${movie.id}`"
        >{{ movie.id }} {{ movie.title }}</router-link
      >
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "MoviesDb",
  data() {
    return {
      movies: [],
    };
  },
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/top_rated?api_key=7417015bd49ede14978e21e667b247e6"
      )
      .then((response) => {
        this.movies = response.data.results;
        console.log(this.movies);
      });
  },
};
</script>
