<template>
  <v-app>
    <Header />

    <v-content>
      <TableView />
    </v-content>
  </v-app>
</template>

<script>
import Header from "./components/Header";
import TableView from "./components/TableView";

export default {
  name: "App",

  components: {
    Header,
    TableView
  },

  data: () => ({
    //
  })
};
</script>
