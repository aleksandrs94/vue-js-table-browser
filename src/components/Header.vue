<template>
  <v-app-bar app dark src="https://picsum.photos/1920/1080?random">
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

      <v-toolbar-title class="shrink mt-1 hidden-sm-and-down">
        TableBrowser
      </v-toolbar-title>
    </div>

    <v-spacer />

    <div>
      <Version />
    </div>
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
