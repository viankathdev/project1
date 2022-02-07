<template>
    <div>
      <!-- Task table begin here -->
      <v-col class="ma-0 pa-0">
        <v-card>
          <v-card-title>Tutorials</v-card-title>
          <v-data-table
            :headers="headers"
            :items="tasks"
            :items-per-page="5"
          >
            <template v-slot:item.task_status="{ item }">
              <v-chip
                small
                :color="getColor(item.task_status)"
                dark
              >
                {{ item.task_status }}
              </v-chip>
            </template>
            <template v-slot:[`item.actions`]="{ item }" class="d-flex d-inline-flex">
              <div class="text-left d-flex">
                  <TaskView v-bind:task=item />
                  <v-icon 
                    small 
                    class="mr-2" 
                    :disabled="editBtnDisable"
                    color="green lighten-1"
                    @click="onUpdateTask(item)">mdi-pencil</v-icon>
                  <v-icon 
                    small 
                    class="mr-2" 
                    :disabled="editBtnDisable"
                    color="red lighten-1"
                    @click="removeItem(item)">mdi-delete</v-icon>
                </div>
            </template>
          </v-data-table>
        </v-card>
      </v-col>
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
        snackbar: false,
        items: [],
        title: "",
        headers: [
          { text: "Title", align: "start", sortable: true, value: "title" },
          { text: "Status", value: "task_status", sortable: true },
          { text: "Actions", value: "actions", sortable: false },
        ],
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
          this.items = response.map(this.getDisplayTasks);
          console.log(response);
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
        },
        getDisplayTasks(task) {
          return {
            id: task.id,
            title: task.title.length > 30 ? task.title.substr(0, 30) + "..." : task.title,
            status: task.task_status,
          };
        },
        getColor (status) {
          if (status == 'Pending') return 'deep-orange'
          else if (status == 'In Progress') return 'amber'
          else return 'blue'
        },
    },
    mounted(){
      // Initialize method to populate task table
      this.getAllTask()
    }
  };
</script>