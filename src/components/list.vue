<template>
  <v-card
    max-width="450"
    class="mx-auto"
    
  >
    <v-toolbar
      :color="tcolor"
      dark
    >
      <v-toolbar-title>{{ title }}</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-plus</v-icon>
      </v-btn>

    </v-toolbar>

    <v-list three-line>
      <template v-for="(item, index) in items">
        <v-list-item
          :key="item.id"
        >
          <v-list-item-content>
            <v-list-item-title>{{ item.title }} <span class="grey--text text--lighten-1">{{ item.comments.length }}</span></v-list-item-title>
            <v-list-item-subtitle v-html="item.comments[item.comments.length-1]"></v-list-item-subtitle>
          </v-list-item-content>

          <v-list-item-icon>
            <v-btn icon>
              <v-icon>mdi-pencil</v-icon>
            </v-btn>
          </v-list-item-icon>
        </v-list-item>

        <v-divider
          :key="index"
        ></v-divider>
      </template>
    </v-list>
  </v-card>
</template>

<script>
  export default {
    props: ['title', 'tcolor', 'items'],
    data: () => ({
      //
    }),
  }
</script>