<template>
  <v-card flat color="dark" class="mb-5" >
    <v-row>
      <v-col cols="5">
        <v-card :to="to" rounded="lg">
          <v-img height="215" :src="poster">
            <v-chip color="primary" small class="ma-2 float-right">
              <v-icon class="mr-1">mdi-clock</v-icon>
              {{ runtime }}</v-chip
            >
          </v-img>
        </v-card>
      </v-col>

      <v-col cols="7">
        <h4 class="text-uppercase font-weight-bold mb-1">{{ title }}</h4>
        <h4 class="mb-2">({{ year }})</h4>

        <h5 class="mb-2">{{ genre }}</h5>

        <div class="d-flex flex-row align-center mb-2">
          <v-icon small color="yellow" class="mr-1">mdi-star</v-icon>
          <h5>{{ rating }}</h5>
        </div>
      </v-col>
    </v-row>
  </v-card>
</template>
<script>
export default {
  props: {
    poster: {
      type: String,
      default: () => undefined,
    },
    title: {
      type: String,
      default: () => undefined,
    },
    year: {
      type: String,
      default: () => undefined,
    },
    runtime: {
      type: String,
      default: () => undefined,
    },
    genre: {
      type: String,
      default: () => undefined,
    },
    rating: {
      type: String,
      default: () => undefined,
    },
    to: {
      type: String,
      default: () => undefined,
    },
  },
}
</script>
