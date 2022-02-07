<template>
  <v-row class="mt-4">
    <v-row >
       <v-card
        width=100%
        class="d-flex justify-space-between align-center mb-6"
        flat
        tile
      >
        <h2 class="tasks-h2 py-5">Kickstart your next project, <br> create now.</h2>
        <v-img 
          max-width="500"
          src="/task-women.png"
        ></v-img>
      </v-card>
    </v-row>
    <v-col><TaskForm @refreshList="refreshList" :isEdit="isEdit" :task="task"/>
    </v-col>
    <v-col><TaskTable :isRefreshList="isRefreshList" @editTask="editTask"/></v-col>
  </v-row>
</template>

<script>
export default {
  name: 'TasksPage',
  data() {
        return {
            isRefreshList: false,
            isEdit: false,
            task: []
        };
    },
  methods: {
    refreshList() {
      this.isRefreshList = !this.isRefreshList;
      this.isEdit = false;
    },
    editTask(task_item) {
      this.isEdit = true;
      this.task = task_item;
    }
  }
}
</script>
<style scoped>
  .tasks-h2 {
    font-size: 2.5em;
  }
</style>