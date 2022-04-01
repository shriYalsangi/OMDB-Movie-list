<template>
  <li class="list-group-item media" @click="onMovieSelect">
    <img :src="thumbnailURL" width="50" height="80" class="mr-3" />
    <div class="media-body mr-9">
      <h2>{{ movie.Title }}</h2>
      <div>({{ movie.Year }})</div>
    </div>
  </li>
</template>

<script>
export default {
  name: 'MovieListItem',
  props: {
    movie: Object,
  },
  computed: {
    thumbnailURL() {
      return this.movie.Poster;
    },
  },
  methods: {
    onMovieSelect() {
      this.$emit('movieSelect', this.movie.imdbID);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
li img {
  margin-right: 1rem;
}
li div {
  display: flex;
  flex-direction: column;
}
</style>
