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
     <v-btn class="mr-3" light><router-link class="nav-link" to="/leaderboard">Leaderboard</router-link>
     </v-btn>
     <v-avatar
      color="secondary"
      size="42"
    ></v-avatar>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>
