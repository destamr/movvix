<template>
  <v-app dark>
    <v-app-bar color="dark" fixed app>
      <v-toolbar-title to="/">
        <v-img :src="logo" width="100" contain />
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <v-col cols="4">
        <m-text-field
          placeholder="Search"
          append-icon="mdi-magnify"
          class="mr-2"
        />
      </v-col>

      <!--      <div>-->
      <!--        <v-tabs background-color="dark" hide-slider right>-->
      <!--          <v-tab v-for="(menu, index) in menus" :key="index">-->
      <!--            <h5 class="text-capitalize">{{ menu.title }}</h5>-->
      <!--          </v-tab>-->
      <!--        </v-tabs>-->
      <!--      </div>-->
    </v-app-bar>

    <v-main>
      <v-fade-transition>
        <nuxt keep-alive />
      </v-fade-transition>
    </v-main>

    <v-footer color="dark">
      <v-spacer />
      <span>&copy; {{ new Date().getFullYear() }} - Daisy Tamara</span>
    </v-footer>
  </v-app>
</template>

<script>
import MTextField from '../components/forms/MTextField'
export default {
  components: { MTextField },
  data: () => ({
    logo: require('assets/images/logo.svg'),
    menus: [
      { title: 'Movies', to: '/' },
      { title: 'TV Series', to: '/' },
      { title: 'Genre', to: '/' },
      { title: 'Year', to: '/' },
    ],
  }),
}
</script>
<style lang="scss">
.v-main__wrap {
  background-color: #080405 !important;
}
</style>
