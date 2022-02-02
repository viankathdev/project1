<template>
  <v-row>
    <v-col>
      <img
        src="/v.png"
        alt="Vuetify.js"
        class="mb-5"
      >
      <h2>Tasks</h2>
      <br>
      <v-simple-table>
        <template v-slot:default>
        <thead>
            <tr>
            <th class="text-left">
                Tasks
            </th>
            <th class="text-left">
                Status
            </th>
             <th class="text-left">
                Action
            </th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Task #1</td>
                <td>
                    <v-btn
                    class="ma-2"
                    text
                    icon
                    color="green lighten-2"
                    >
                    <v-icon>mdi-check-circle-outline</v-icon>
                </v-btn>
                </td>
                <td>
                    <v-btn
                    color="primary"
                    nuxt
                    outlined
                    to="/task-one"
                    >
                    <v-icon left>
                        mdi-eye
                    </v-icon>
                    View
                    </v-btn>
                </td>
            </tr>
            <tr>
                <td>Task #2</td>
                <td>
                        <v-btn
                        class="ma-2"
                        text
                        icon
                        color="green lighten-2"
                        >
                        <v-icon>mdi-check-circle-outline</v-icon>
                    </v-btn>
                </td>
                <td>
                    <v-btn
                    color="primary"
                    outlined
                    nuxt
                    to="/task-two"
                    >
                    <v-icon left>
                        mdi-eye
                    </v-icon>
                    View
                    </v-btn>
                </td>
            </tr>
            <tr>
                <td>Task #3</td>
                <td>
                        <v-btn
                        class="ma-2"
                        text
                        icon
                        color="green lighten-2"
                        >
                        <v-icon>mdi-check-circle-outline</v-icon>
                    </v-btn>
                </td>
                <td>
                    <v-btn
                    color="primary"
                    outlined
                    nuxt
                    to="/task-three"
                    >
                    <v-icon left>
                        mdi-eye
                    </v-icon>
                    View
                    </v-btn>
                </td>
            </tr>
        </tbody>
        </template>
    </v-simple-table>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'TaskPage'
}
</script>
