<template>
  <div v-if="movie" class="col-md-8">
    <header class="movie_detail_header">
      <h1 data-test="movie-title">{{ movie.title }}</h1>
      <h2 data-test="movie-year">({{ movie.year }})</h2>
    </header>
    <section id="movie_detailed_view" class="row">
      <div class="poster_cast col-md-5">
        <img
          v-if="movie.poster !== 'N/A'"
          :src="movie.poster"
          class="movie_poster"
        />
        <img
          v-else
          src="https://via.placeholder.com/300x300"
          class="movie_poster"
        />
        <div class="row">
          <div class="column">
            <dt>Language</dt>
            <dd data-test="movie-language">{{ movie.language }}</dd>
          </div>
          <div class="column">
            <dt>Duration</dt>
            <dd data-test="movie-duration">{{ movie.duration }}</dd>
          </div>
        </div>
        <div class="row">
          <div class="column">
            <dt>Cast</dt>
            <dd v-for="cast in movie.cast" :key="cast">{{ cast }}</dd>
          </div>
        </div>
      </div>
      <div class="movie_plot col-md-7">
        <h2>Synopsis</h2>
        <p data-test="movie-plot">{{ movie.plot }}</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'MovieDetail',
  props: ['movie'],
};
</script>
