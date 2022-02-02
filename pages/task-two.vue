<template>
  <v-row>
    <v-col>
        <img
            src="/v.png"
            alt="Vuetify.js"
            class="mb-5"
        >
        <h2 class="py-5">Task #2 | Create Nuxt Vue Js Project</h2>
        <p>When you run npx create-nuxt-app project1 in CLI, please select these options:</p>
        <ul class="mb-5">
            <li>Programming languages - <b>JS</b></li>
            <li>Package manager: <b>NPM</b></li>
            <li>UI Framework: <b>Vuetify</b></li>
            <li>Nuxtjs Modules: <b>Axios</b></li>
            <li>Linting Tools: <b>none</b></li>
            <li>Testing Framework: <b>none</b></li>
            <li>Rendering Mode: <b>SSR</b></li>
            <li>Deployment Target: <b>Server</b></li>
            <li>Development Tools: <b>jsconfig.json</b></li>
            <li>What is your Github username: <b>enter you GitHub></b></li>
            <li>Version Control System: <b>Git</b></li>
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
  name: 'TaskTwoPage'
}
</script>
