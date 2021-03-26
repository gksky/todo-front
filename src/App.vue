<template>
  <v-app>
    <v-container>
      <v-row class="">
        <v-col cols="4">
          <List title="TODO" tcolor="orange darken-4" :items="todo"/>
        </v-col>

        <v-col cols="4">
          <List title="DOING" tcolor="green darken-4" :items="doing"/>
        </v-col>

        <v-col cols="4">
          <List title="DONE" tcolor="blue darken-4" :items="done"/>
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
    todo: [],
    doing: [],
    done: [],
    items: [
      {
        id: 11,
        date: '2021-03-20',
        list: 'todo',
        title: 'Summer BBQ',
        comments: [
          `Wish I could come, but I'm out of town this weekend.`,
          `Wish I could come, but I'm out of town this weekend.`,
        ]
      },
      {
        id: 10,
        date: '2021-02-20',
        list: 'doing',
        title: 'Summer BBQ',
        comments: [
          `Wish I could come, but I'm out of town this weekend.`,
        ]
      },
      {
        id: 12,
        date: '2021-02-24',
        list: 'doing',
        title: 'Summer BBQ',
        comments: [
          `Wish I could come, but I'm out of town this weekend.`,
        ]
      },
      {
        id: 13,
        date: '2021-01-20',
        list: 'done',
        title: 'Summer BBQ',
        comments: [
          `Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.`,
          `Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.`,
          `Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.`,
        ]
      },
    ]

  }),
  created: function () {
    this.todo = this.items.filter(item => item.list == 'todo')
    this.doing = this.items.filter(item => item.list == 'doing')
    this.done = this.items.filter(item => item.list == 'done')
  }

};
</script>
