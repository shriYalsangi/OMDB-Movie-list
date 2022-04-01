<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"> </SearchBar>
    <div class="row">
      <MovieList :movies="movies" @movieSelect="onMovieSelect"> </MovieList>
      <MovieDetail :movie="selectedMovie"></MovieDetail>
    </div>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';
import MovieDetail from './components/MovieDetail.vue';
import axios from 'axios';

const API_KEY = '1d333855';

export default {
  name: 'App',
  components: {
    SearchBar,
    MovieList,
    MovieDetail,
  },
  data() {
    return {
      movies: [],
      movie: {
        title: '',
        year: '',
        imdbID: '',
        poster: '',
        language: '',
        duration: 0,
        cast: [],
        plot: '',
      },
      selectedMovie: null,
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get('http://www.omdbapi.com/', {
          params: {
            apikey: API_KEY,
            type: 'movie',
            page: 1,
            s: searchTerm,
          },
        })
        .then((res) => {
          this.movies = res.data.Search;
        });
    },
    onMovieSelect(imdbID) {
      axios
        .get('http://www.omdbapi.com/', {
          params: {
            apikey: API_KEY,
            plot: 'full',
            i: imdbID,
          },
        })
        .then((res) => {
          this.movie = {
            imdbID,
            title: res.data.Title,
            year: res.data.Year,
            poster: res.data.Poster,
            language: res.data.Language,
            duration: res.data.Runtime,
            cast: res.data.Actors.split(','),
            plot: res.data.Plot,
          };
          this.selectedMovie = this.movie;
        });
    },
  },
};
</script>
