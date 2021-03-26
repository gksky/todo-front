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
        list: 'todo',
        title: 'Summer BBQ',
        comments: [
          `Wish I could come, but I'm out of town this weekend.`,
          `Wish I could come, but I'm out of town this weekend.`,
        ]
      },
      {
        id: 12,
        list: 'doing',
        title: 'Summer BBQ',
        comments: [
          `Wish I could come, but I'm out of town this weekend.`,
        ]
      },
      {
        id: 13,
        list: 'done',
        title: 'Summer BBQ',
        comments: [
          `Wish I could come, but I'm out of town this weekend.`,
          `Wish I could come, but I'm out of town this weekend.`,
          `Wish I could come, but I'm out of town this weekend.`,
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
