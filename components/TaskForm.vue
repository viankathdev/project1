<template>
  <v-card
    class="pa-4 mb-10"
    outlined
  >
    <!-- Create and update form -->
    <v-form>
      <v-container>
        <v-row>
          <v-col
            cols="12"
          >
            <v-text-field
              hide-details="true"
              v-model="title"
              label="Title"
              outlined
            ></v-text-field>
          </v-col>
          <v-col
            cols="12"
          >
          <v-textarea
            v-model="description"
            hide-details="true"
            label="Description"
            auto-grow
            outlined
            rows="3"
          ></v-textarea>

          <v-col cols="12 pa-0 pt-4">
            <v-select
              v-model="task_status"
              :items="['Pending', 'In Progress', 'Completed']"
              label="Status"
              outlined
            ></v-select>
          </v-col>
        </v-col>
        <v-btn
          class="ma-2"
          color="orange lighten-2"
          @click="isEdit ? updateTask() : addTask()" 
          :disabled="!description || !title"
        >
          {{btnLabel}} Task
        </v-btn>
         <v-btn
          v-if="isEdit"
          class="ma-2"
          color="grey lighten-2"
          @click="cancelEdit" 
        >
          Cancel
        </v-btn>
        </v-row>
      </v-container>
    </v-form>
    <!-- Method notification -->
    <v-snackbar
      v-model="snackbar"
      top
      right
      color="green darken-2"
      >
      {{message}}
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
  </v-card>
</template>

<script>
  import axios from "axios";
  export default {
    name: "TaskForm",
    props: ['isEdit', 'task'],
    data() {
      return {
        status_option: ['Pending', 'In Progress', 'Completed'],
        title: "",
        description: "",
        task_status: "",
        btnLabel: 'Create',
        snackbar: false,
        message: 'Task successfully created.'
      };
    },
    watch: {
      // Enable edit form and populate fields
      isEdit () {
        if (this.isEdit) {
          // Populate Form
          this.message = 'Task successfully updated.'
          this.title = this.task.title
          this.description = this.task.description
          this.task_status = this.task.task_status
          this.btnLabel = 'Update'

        } 
      },
    },
    methods: {
      // Add/create task
      async addTask() {
        const response = await this.$axios.post("/tasks", {
          title: this.title,
          description: this.description,
          task_status: this.task_status,
          status: 'active'
        });
        this.snackbar = true
        this.clearForm()
        
      },
      // Update task
      async updateTask() {
          const response = await this.$axios.put("/tasks/" + this.task._id, {
          title: this.title,
          description: this.description,
          task_status: this.task_status
        });
        this.snackbar = true
        this.clearForm()
      },
      // Cancels edit, clear forms
      cancelEdit () {
        this.clearForm()
      },
      // Clear field forms and initialize data
      clearForm () {
        this.$emit('refreshList')
        this.title = "";
        this.description = "";
        this.task_status = "";
        this.btnLabel = 'Create'
        this.message = 'Task successfully created.'
      }
    }
  };
</script>