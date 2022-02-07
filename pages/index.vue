<template>
  <v-row class="home-row">
    <v-col class="mt-16 pt-10">
      <div class="text-center">
        <h1 class="h1-home mb-4">Organize it all <br> with Task Track</h1>
        <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit</p>
         <v-btn
            class="ma-5"
            outlined
            color="red"
            nuxt
            to="/tasks"
          >
          Get Started
          </v-btn>
      </div>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>

<style scoped>
  .home-row {
    height: 90vh;
    background: url('/taskhome-featured.png');
    background-size: 80%;
    background-repeat: no-repeat;
    background-position: bottom;
  }
  .h1-home {
    font-size: 4.5em;
    line-height: 1.3;;
  }
</style>