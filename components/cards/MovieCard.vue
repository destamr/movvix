<template>
  <v-card rounded="lg" class="mx-auto" height="300" :to="to">
    <v-img
      :src="poster"
      gradient="0deg, #480101, transparent 40%"
      height="300"
    >
      <div
        class="align-content-space-between fill-height"
        style="display: grid"
      >
        <v-card-title>
          <v-spacer />
          <v-chip color="primary" small>
            <v-icon class="mr-1">mdi-clock</v-icon>
            200 min</v-chip
          >
        </v-card-title>
        <v-card-text>
          <h5 class="text-center font-weight-bold">{{ title }}</h5>
          <h5 class="text-center">({{ year }})</h5>
        </v-card-text>
      </div>
    </v-img>
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
    to: {
      type: String,
      default: () => undefined,
    },
  },
  data: () => ({
    reveal: false,
  }),
}
</script>
