<template>
  <v-app>
    <v-container>
      <v-row class="">
        <v-col cols="4">
          <List title="TODO" tcolor="orange darken-4" :items="todo" @sendData="sendData($event)"/>
        </v-col>

        <v-col cols="4">
          <List title="DOING" tcolor="green darken-4" :items="doing" @sendData="sendData($event)"/>
        </v-col>

        <v-col cols="4">
          <List title="DONE" tcolor="blue darken-4" :items="done" @sendData="sendData($event)"/>
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
    items: [],
  }),
  methods: {
    async sendData(record) {
      try {
        await fetch('http://localhost/api.php', {
          method: 'POST',
          body: JSON.stringify(record),
          headers: {
            'Content-Type': 'application/json'
          }
        });
      } catch (error) {
        console.error('Ошибка:', error);
      }

      this.getData()
    },
    filter() {
      this.todo = this.items.filter(item => item.status == 'todo')
      this.doing = this.items.filter(item => item.status == 'doing')
      this.done = this.items.filter(item => item.status == 'done')
    },
    async getData() {
      const f = await fetch('http://localhost/api.php')
      this.items = await f.json()
      this.filter()
    }
  },
  created() {
    this.getData()
  }

};
</script>
