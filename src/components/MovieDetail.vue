<template>
  <div>
    <h1>{{ movieobj.title }}</h1>
    <p>{{ movieobj.overview }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "MovieDetail",
  data() {
    return {
      id: this.$route.params.id,
      movieobj: Object,
    };
  },
  mounted() {
    let request = `https://api.themoviedb.org/3/movie/${this.id}?api_key=7417015bd49ede14978e21e667b247e6`;
    console.log(request);
    axios.get(request).then((response) => {
      console.log(response);
      this.movieobj = response.data;
    });
  },
};
</script>
