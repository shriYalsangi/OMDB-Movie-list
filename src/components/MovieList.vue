<template>
  <div class="col-md-4">
    <ul class="list-group">
      <MovieListItem
        v-for="movie in movies"
        :key="movie.imdbID"
        :movie="movie"
        @movieSelect="onMovieSelect"
      ></MovieListItem>
    </ul>
  </div>
</template>

<script>
import MovieListItem from './MovieListItem.vue';

export default {
  name: 'MovieList',
  components: {
    MovieListItem,
  },
  props: {
    movies: Array,
  },
  methods: {
    onMovieSelect(imdbID) {
      this.$emit('movieSelect', imdbID);
    },
  },
};
</script>

<style scoped></style>
