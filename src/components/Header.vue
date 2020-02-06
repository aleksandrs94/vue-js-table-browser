<template>
  <v-app-bar
    app
    dark
    src="https://picsum.photos/1920/1080?random"
    scroll-target="#scrolling-techniques-2"
  >
    <template v-slot:img="{ props }">
      <v-img
        v-bind="props"
        gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
      ></v-img>
    </template>
    <div class="d-flex align-center">
      <v-img
        alt="Vuetify Logo"
        class="shrink mr-2"
        contain
        src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
        transition="scale-transition"
        width="40"
      />

      <v-title class="shrink mt-1 hidden-sm-and-down">TableBrowser</v-title>
    </div>

    <v-spacer />

    <v-text>
      <Version />
    </v-text>
  </v-app-bar>
</template>

<script>
import Version from "./Version";

export default {
  name: "Header",

  components: {
    Version
  }
};
</script>
