<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="4">
        <v-card rounded="lg">
          <v-img height="500" :src="movie.Poster" />
        </v-card>
      </v-col>

      <v-col cols="12" md="8">
        <div class="align-center d-flex flex-row">
          <h1 class="font-weight-bold mr-2">
            {{ movie.Title }}
          </h1>
          <div class="align-center d-flex flex-row">
            <v-icon color="yellow" class="mr-2">mdi-star</v-icon>
            <h2>{{ movie.imdbRating }}</h2>
          </div>
        </div>

        <h3 class="mb-2">({{ movie.Year }})</h3>

        <h4 class="mb-2">{{ movie.Genre }}</h4>

        <v-chip small color="primary" class="mb-2">
          <v-icon left>mdi-clock</v-icon>
          {{ movie.Runtime }}
        </v-chip>

        <h4>{{ movie.Plot }}</h4>

        <div class="mt-4">
          <h5>Director: {{ movie.Director }}</h5>
          <h5>Writer: {{ movie.Writer }}</h5>
          <h5>Actors: {{ movie.Actors }}</h5>
          <h5>Released: {{ movie.Released }}</h5>
          <h5>Language: {{ movie.Language }}</h5>
          <h5>Production: {{ movie.Production }}</h5>
          <h5>Awards: {{ movie.Awards }}</h5>
          <h5>BoxOffice: {{ movie.BoxOffice }}</h5>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      movie: {
        Poster: null,
        Title: null,
        imdbRating: null,
        Year: null,
        Genre: null,
        Runtime: null,
        Plot: null,
        Released: null,
        Director: null,
        Writer: null,
        Language: null,
        Production: null,
        Awards: null,
        BoxOffice: null,
      },
    }
  },
  head: { title: 'Detail' },
  created() {
    fetch(
      `https://www.omdbapi.com/?apikey=faf7e5bb&plot=full&i=${this.$route.params.id}`
    )
      .then((json) => json.json())
      .then((res) => (this.movie = res))
      .catch((e) => console.log(e))
  },
}
</script>
