<template>
  <v-app>
    <v-container>
      <v-row class="">
        <v-col cols="4">
          <List title="TODO" tcolor="orange darken-4"/>
        </v-col>

        <v-col cols="4">
          <List title="DOING" tcolor="green darken-4"/>
        </v-col>

        <v-col cols="4">
          <List title="DONE" tcolor="blue darken-4"/>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import List from './components/list';

export default {
  name: 'App',

  components: {
    List,
  },

  data: () => ({
    //
  }),
};
</script>
