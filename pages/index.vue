<template>
  <v-row>
    <v-col>
      <div class="logo text-center mb-10">
        <NuxtLogo />
        <VuetifyLogo />
      </div>
      <div class="text-center">
        <h2>Welcome to the Vuetify + Nuxt.js task</h2>
        <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
      </div>
      <v-row class="mt-10">
        <v-col cols="12" sm="4">
          <v-card
            class="mx-auto"
            max-width="344"
          >
            <v-card-text>
              <div>Task #1</div>
              <p class="text-h4 text--primary">
                Create Github Account
              </p>
              <div class="text--primary">
                Lorem ipsum dolor sit amet consectetur elit<br>
                Minus quaerat temporibus pariatur Quam eos.
              </div>
            </v-card-text>
            <v-card-actions>
              <NuxtLink class="ma-2" color="success" to="/task-one">View</NuxtLink>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="12" sm="4">
          <v-card
            class="mx-auto"
            max-width="344"
          >
            <v-card-text>
              <div>Task #2</div>
              <p class="text-h4 text--primary">
                Create Nuxt Vue Js Project
              </p>
              <div class="text--primary">
                Lorem ipsum dolor sit amet consectetur elit<br>
                Minus quaerat temporibus pariatur Quam eos.
              </div>
            </v-card-text>
            <v-card-actions>
              <NuxtLink to="/task-two">View</NuxtLink>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="12" sm="4">
          <v-card
            class="mx-auto"
            max-width="344"
          >
            <v-card-text>
              <div>Task #3</div>
              <p class="text-h4 text--primary">
                Create Pages
              </p>
              <div class="text--primary">
                Lorem ipsum dolor sit amet consectetur elit<br>
                Minus quaerat temporibus pariatur Quam eos.
              </div>
            </v-card-text>
            <v-card-actions>
              <NuxtLink to="/task-three">View</NuxtLink>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
