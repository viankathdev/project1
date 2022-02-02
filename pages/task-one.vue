<template>
  <v-row>
    <v-col>
      <img
        src="/v.png"
        alt="Vuetify.js"
        class="mb-5"
      >
      <h2>Task #1 | Create Github Account</h2>
      <br>
      <ul>
        <li>Create Github using your vian@nathanhr.com account. </li>
        <li>Install github desktop or any git tools you prefer </li>
        <li>Add your vian@nathanhr.com github login account in your local machine. </li>
        <li>https://github.com/ </li>
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
  name: 'TaskOnePage'
}
</script>
