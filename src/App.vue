<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
     <v-app-bar-nav-icon class="mx-6" tile v-for="item in 7" :key="item">Level {{item}}
     </v-app-bar-nav-icon>
     <v-spacer></v-spacer>
     <v-avatar
      color="secondary"
      size="42"
    ></v-avatar>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',

  components: {
    HelloWorld
  },

  data: () => ({
    //
  })
}
</script>
