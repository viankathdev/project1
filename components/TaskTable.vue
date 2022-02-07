<template>
    <div>
      <!-- Task table begin here -->
      <v-simple-table class="elevation-2" fixed-header height="500px">
        <template v-slot:default>
              <thead>
                  <tr>
                  <th class="text-left text-h6">
                      Tasks
                  </th>
                  <th class="text-left text-h6">
                      Status
                  </th>
                  <th class="text-left text-h6">
                      Action
                  </th>
                  </tr>
              </thead>
              <tbody>
                <tr v-for="task in tasks" :key="task.id">
                  <td>{{task.title}}</td>
                  <td>
                    <p v-if="task.task_status === 'Pending'" class="deep-orange--text text--lighten--1 mb-0">{{task.task_status}}</p>
                    <p v-if="task.task_status === 'In Progress'" class="amber--text text--darken--10 mb-0">{{task.task_status}}</p>
                    <p v-if="task.task_status === 'Completed'" class="blue--text text--lighten--1 mb-0">{{task.task_status}}</p>
                  </td>
                  <td class="text-left d-flex">
                    <TaskView v-bind:task=task />
                    <div class="del-btn">
                      <v-btn
                        class="ma-1"
                        outlined
                        fab
                        x-small
                        :disabled="editBtnDisable"
                        color="green lighten-1"
                        @click="onUpdateTask(task)"
                      >
                        <v-icon>mdi-pencil</v-icon>
                      </v-btn>
                    </div>
                    <div class="del-btn">
                      <v-btn
                        class="ma-1"
                        outlined
                        fab
                        x-small
                        color="red lighten-1"
                        @click="removeItem(task)"
                      >
                        <v-icon>mdi-delete-empty</v-icon>
                      </v-btn>
                    </div>
                </td>
                </tr>
              </tbody>
          </template>
      </v-simple-table>
      <!-- Task table end here -->
      <!-- On delete notification -->
      <v-snackbar
        v-model="snackbar"
        top
        right
        color="deep-orange darken-2"
        >
        Task successfully deleted.
        <template v-slot:action="{ attrs }">
          <v-btn
            color="white"
            text
            v-bind="attrs"
            @click="snackbar = false"
          > x
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
  import axios from "axios";
  export default {
    name: "TaskTable",
    props: ['isRefreshList'],
    data() {
      return {
        tasks: [],
        editBtnDisable: false,
        snackbar: false
      };
    },
    watch: {
      isRefreshList () {
        this.getAllTask();
        this.editBtnDisable = false
      },
    },
    methods: {
        // Get all task from Task API
        async getAllTask () {
          const response = await this.$axios.$get('/tasks');
          this.tasks = response;
        },
        // Remove and delete task
        async removeItem(task) {
          await this.$axios.$delete("/tasks/" + task._id);
          this.snackbar = true
          this.getAllTask()
        },
        // On edit task, set edit form to true
        onUpdateTask (task) {
          this.$emit('editTask', task)
          this.editBtnDisable = true
        }
    },
    mounted(){
      // Initialize method to populate task table
      this.getAllTask()
    }
  };
</script>