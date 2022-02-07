<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="600"
    >
      <template v-slot:activator="{ on, attrs }">
          <v-btn
            class="ma-1"
            outlined
            fab
            x-small
            color="blue lighten-1"
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-eye</v-icon>
          </v-btn>
      </template>
      <v-card>
        <div class="pa-4 d-flex flex-no-wrap justify-space-between align-center">
          <v-col cols="6" md="4">
            <v-img
              src="https://images.ctfassets.net/dm4oa8qtogq0/3ergI5xlKNW3NDpOzEBXvG/6bd9708ed460a6766d6fe30add8b37e8/template-annual-review.jpg?w=192&fm=webp"
            ></v-img> </v-col>
          <v-col>
              <v-card-title class="text-h4" style="word-break: inherit;">
              {{task.title}}
            </v-card-title>
            <v-card-text>
              <p style="white-space: pre-line;">{{task.description}}</p>
            </v-card-text>
            <div>
              <span v-if="task.task_status === 'Pending'" class="deep-orange--text ms-3 task-status-chip">{{task.task_status}}</span>
              <span v-if="task.task_status === 'In Progress'" class="amber--text ms-3 task-status-chip">{{task.task_status}}</span>
              <span v-if="task.task_status === 'Completed'" class="blue--text ms-3 task-status-chip">{{task.task_status}}</span>
            </div>
          </v-col>
        </div>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="dialog = false"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    props: ['task'],
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>

<style scoped>
  .task-status-chip {
    border: 1px solid;
    padding: 8px 24px;
    border-radius: 8px;
    font-size: 14px;
  }
</style>