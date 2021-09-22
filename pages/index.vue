<template>
  <v-container fluid>
    <v-row>
      <v-col cols="12" md="8">
        <v-card rounded="lg">
          <v-carousel
            cycle
            hide-delimiter-background
            show-arrows-on-hover
            hide-delimiters
            height="500"
          >
            <v-carousel-item
              v-for="(recentMovie, id) in recentMovies"
              :key="id"
              :src="recentMovie.Poster"
            >
              <v-card-text class="fill-height pa-8 align-end d-flex">
                <div>
                  <h2 class="font-weight-bold">{{ recentMovie.Title }}</h2>

                  <h3 class="mb-1">({{ recentMovie.Year }})</h3>

                  <h5 class="mb-2">{{ recentMovie.Genre }}</h5>

                  <v-btn
                    small
                    light
                    depressed
                    class="text-capitalize font-weight-bold"
                    color="primary"
                    >See Details</v-btn
                  >
                </div>
              </v-card-text>
            </v-carousel-item>
          </v-carousel>
        </v-card>
      </v-col>

      <v-col cols="12" md="4">
        <h4 class="font-weight-bold mb-4">Popular Movies</h4>

        <popular-movies
          v-for="(movie, id) in movies"
          :key="id"
          :poster="movie.Poster"
          :title="movie.Title"
          :year="movie.Year"
          :runtime="movie.Runtime"
          :rating="movie.imdbRating"
          :genre="movie.Genre"
          :to="movie.imdbID"
        />
      </v-col>

      <v-col cols="12">
        <h3>Recommendations</h3>
      </v-col>

      <v-col
        v-for="(recommendation, id) in recommendations"
        :key="id"
        cols="6"
        md="2"
      >
        <movie-card
          :poster="recommendation.Poster"
          :title="recommendation.Title"
          :year="recommendation.Year"
          :to="recommendation.imdbID"
        />
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import MovieCard from '../components/cards/MovieCard'
import PopularMovies from '../components/cards/PopularMovies'

export default {
  components: { MovieCard, PopularMovies },

  data() {
    return {
      recentMovies: [],
      movies: [],
      recommendations: [],
    }
  },

  head: { title: 'Home' },

  created() {
    const popularMovies = ['tt0304141', 'tt1475582']

    // eslint-disable-next-line array-callback-return
    popularMovies.map((movieId) => {
      fetch(`https://www.omdbapi.com/?apikey=faf7e5bb&i=${movieId}`)
        .then((json) => json.json())
        .then((res) => this.movies.push(res))
        .catch((e) => console.log(e))
    })

    const recentMovies = ['tt6566576', 'tt9701940', 'tt9701942']

    // eslint-disable-next-line array-callback-return
    recentMovies.map((movieId) => {
      fetch(`https://www.omdbapi.com/?apikey=faf7e5bb&i=${movieId}`)
        .then((json) => json.json())
        .then((res) => this.recentMovies.push(res))
        .catch((e) => console.log(e))
    })

    const recommendations = [
      'tt6566576',
      'tt9701940',
      'tt9701942',
      'tt0045152', // Signin in the Rain
      'tt0111161', // The Shawshank Redemption
      'tt0108778', // Friends
      'tt0110413', // Léon: The Professional
      'tt0304141', // Harry Potter and the Prisoner of Azkaban
      'tt0434409', // V for Vendetta
      'tt0460649', // How I Met Your Mother
      'tt0972534', // iCarly
      'tt0898266', // The Big Bang Theory
      'tt1187043', // 3 Idiots
      'tt1475582', // Sherlock
      'tt1504320', // The King's Speech
      'tt1375666', // Inception
      'tt0848228', // The Avengers
      'tt1670345', // Now You See Me
      'tt0816692', // Interstellar
      'tt3107288', // The Flash
      'tt2084970', // The Imitation Game
      'tt4052886', // Lucifer
      'tt1837492', // 13 Reasons Why
      'tt4555426', // Darkest Hour
      'tt3262342', // Loving Vincent
      'tt7668518', // The Protector
      'tt6966692', // Green Book
      'tt1727824', // Bohemian Rhapsody
    ]

    // eslint-disable-next-line array-callback-return
    recommendations.map((movieId) => {
      fetch(`https://www.omdbapi.com/?apikey=faf7e5bb&i=${movieId}`)
        .then((json) => json.json())
        .then((res) => this.recommendations.push(res))
        .catch((e) => console.log(e))
    })
  },
}
</script>
