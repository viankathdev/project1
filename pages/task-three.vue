<template>
  <v-row>
    <v-col>
        <img
            src="/v.png"
            alt="Vuetify.js"
            class="mb-5"
        >
        <h2>Task #3 | Create Pages</h2>
        <br>
        <p>Create 5 pages under the page folder. See pages below. </p>
        <ul>
            <li><NuxtLink to="/">Home</NuxtLink></li>
            <li><NuxtLink to="/task">Tasks</NuxtLink></li>
            <li><NuxtLink to="/task-one">Task One</NuxtLink></li>
            <li><NuxtLink to="/task-two">Task Two</NuxtLink></li>
            <li><NuxtLink to="/task-three">Task Three</NuxtLink></li>
            <li><NuxtLink to="/about">About</NuxtLink></li>
        </ul>
        <br>
        <v-btn
            class="ma-2"
            outlined
            color="gray"
            nuxt
            to="/"
        >
        Back
        </v-btn>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'TaskThreePage'
}
</script>
