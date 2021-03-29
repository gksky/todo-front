<template>
  <v-card
    class="mx-auto"
    
  >
    <v-toolbar
      :color="tcolor"
      dark
    >
      <v-toolbar-title>{{ title }}</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-dialog
        v-model="dialog"
        persistent
        max-width="600px"
      >
        <template v-slot:activator="{ on, attr }">
          <v-btn icon
            v-bind="attr"
            v-on="on"
            @click="newRecord()"
          >
            <v-icon>mdi-plus</v-icon>
          </v-btn>
        </template>

        <v-card>
          <v-card-title>
            <span class="headline">{{ editable.id }} <span v-if="!editable.id">New</span> Record edit &mdash; {{ editable.tododate }}</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>

                  <v-btn-toggle
                    v-model="editable.status"
                    mandatory
                    color="primary"
                  >
                    <v-btn value="todo">
                      TODO
                    </v-btn>

                    <v-btn value="doing">
                      DOING
                    </v-btn>

                    <v-btn value="done">
                      DONE
                    </v-btn>
                  </v-btn-toggle>

                <v-col cols="12">
                  <v-text-field
                    v-model="editable.title"
                    label="Title*"
                    required
                  ></v-text-field>
                </v-col>
                
                <v-col cols="12">
                  <v-text-field
                    v-model="editable.newComment"
                    label="Comment"
                    required
                  ></v-text-field>
                </v-col>
                
              </v-row>
            </v-container>
            <small>*indicates required field</small>
            <p v-if="editable.comments">Comments:</p>
            <div v-for="(comment, index) in editable.comments" :key="index">
                  {{ index + 1}}. {{ comment }}
                </div>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="blue darken-1"
              text
              @click="dialog = false"
            >
              Close
            </v-btn>
            <v-btn
              color="blue darken-1"
              text
              @click="sendData(); dialog = false"
            >
              Save
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

    </v-toolbar>

    <v-list three-line>
      <template v-for="(item, index) in items">
        <v-list-item
          :key="item.id"
        >
          <v-list-item-content>
            <v-list-item-title>{{ item.title }} <span class="grey--text">{{ item.comments.length }}</span></v-list-item-title>
            <v-list-item-subtitle v-html="item.comments[item.comments.length-1]"></v-list-item-subtitle>
          </v-list-item-content>

          <v-list-item-icon>
            <v-btn icon
              @click="editRecord(index)"
            >
              <v-icon>mdi-pencil</v-icon>
            </v-btn>
            
          </v-list-item-icon>
        </v-list-item>

        <v-divider
          :key="-index"
        ></v-divider>
      </template>
    </v-list>
  </v-card>
</template>

<script>
  export default {
    props: ['title', 'tcolor', 'items'],
    data: () => ({
      dialog: false,
      editable: {},
    }),
    methods: {
      newRecord() {
        const now = new Date()
        this.editable = {tododate: now.toISOString().substring(0, 10), comments: []}
        this.dialog = true
      },
      editRecord(index) {
        this.editable = JSON.parse(JSON.stringify(this.items[index]))
        this.dialog = true
      },
      sendData() {
        this.$emit('sendData', this.editable)
      }
    }
  }
</script>