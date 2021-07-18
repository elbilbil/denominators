<template>
  <v-container>
      <v-row class="mt-4" align="center" justify="center">
        <h1>Leaderboard</h1>
      </v-row>
      <v-row>
          <v-col cols="8">
              <v-card outlined>
                  <v-card-text>
                    <v-row class="text-center flex align-end">
                        <v-col cols="4">
                            <v-card class="space_second_place">
                                <v-card-title class="text-h1 shift_left_2">2</v-card-title>
                                <v-card-text class="ml-2">
                                    <v-row flex justify-space-around>
                                        <v-avatar size="35" class="mr-2 mt-2" :color="winners[1].avatar_color">
                                            <span class="text-h5">{{winners[1].initials}}</span>
                                        </v-avatar>
                                        <div class="mt-1">
                                            <div>
                                                <strong>{{ winners[1].name }}</strong>
                                            </div>
                                            <div class="font-weight-light">
                                                Level {{ winners[1].level }}, XP {{ winners[1].xp }}
                                            </div>
                                        </div>
                                    </v-row>
                                </v-card-text>
                            </v-card>
                        </v-col>
                        <v-col cols="5">
                            <v-card class="space_first_place">
                                <v-card-title class="text-h1">1</v-card-title>
                                <v-card-text class="ml-2">
                                    <v-row flex justify-space-around>
                                        <v-avatar size="35" class="mr-2 mt-2" :color="winners[0].avatar_color">
                                            <span class="text-h5">{{winners[0].initials}}</span>
                                        </v-avatar>
                                        <div class="mt-1">
                                            <div>
                                                <strong>{{ winners[0].name }}</strong>
                                            </div>
                                            <div class="font-weight-light">
                                                Level {{ winners[0].level }}, XP {{ winners[0].xp }}
                                            </div>
                                        </div>
                                    </v-row>
                                </v-card-text>
                            </v-card>
                        </v-col>
                        <v-col cols="3">
                            <v-card class="space_third_place">
                                <v-card-title class="text-h1">3</v-card-title>
                                <v-card-text class="ml-2">
                                    <v-row flex justify-space-around>
                                        <v-avatar size="35" class="mr-2 mt-2" :color="winners[2].avatar_color">
                                            <span class="text-h5">{{winners[2].initials}}</span>
                                        </v-avatar>
                                        <div class="mt-1">
                                            <div>
                                                <strong>{{ winners[2].name }}</strong>
                                            </div>
                                            <div class="font-weight-light">
                                                Level {{ winners[2].level }}, XP {{ winners[2].xp }}
                                            </div>
                                        </div>
                                    </v-row>
                                </v-card-text>
                            </v-card>
                        </v-col>
                    </v-row>
                  </v-card-text>
              </v-card>
          </v-col>
          <v-col cols="4">
              <v-card outlined>
                <v-simple-table class="ma-2">
                    <template v-slot:default>
                    <thead>
                        <tr>
                        <th class="text-left">
                            Rank
                        </th>
                        <th class="text-left">
                            User
                        </th>
                        <th class="text-left">
                            XP
                        </th>
                        <th class="text-left">
                            Location
                        </th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr
                        v-for="user in users"
                        :key="user.name"
                        >
                        <td>{{user.index}}</td>
                        <td>
                            <v-row flex justify-space-around>
                                <v-avatar size="35" class="mr-2 mt-2" :color="user.avatar_color">
                                    <span class="text-h5">{{user.initials}}</span>
                                </v-avatar>
                                <div class="mt-1">
                                    <div>
                                        {{ user.name }}
                                    </div>
                                    <div class="font-weight-light">
                                        Level {{ user.level }}
                                    </div>
                                </div>
                            </v-row>
                        </td>
                        <td>{{ user.xp }}</td>
                        <td>{{ user.location }}</td>
                        </tr>
                    </tbody>
                    </template>
                </v-simple-table>
              </v-card>
          </v-col>
      </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'LeaderBoard',

  data: () => ({
    users: [
      { index: 4, name: 'John Doe', initials: 'JD', level: 6, xp: 1337, location: 'Bangalore', avatar_color: 'red' },
      { index: 5, name: 'Jim Smith', initials: 'JS', level: 7, xp: 1276, location: 'Sidney', avatar_color: 'blue' },
      { index: 6, name: 'Liz Wood', initials: 'LW', level: 6, xp: 1156, location: 'Paris', avatar_color: 'orange' },
      { index: 6, name: 'Laura Test', initials: 'LT', level: 5, xp: 928, location: 'London', avatar_color: 'green' },
      { index: 7, name: 'Nik Lou', initials: 'NL', level: 5, xp: 911, location: 'Hanoi', avatar_color: 'purple' },
      { index: 8, name: 'Ying Xie', initials: 'YX', level: 6, xp: 834, location: 'New York', avatar_color: 'lime' },
      { index: 9, name: 'Pete Foo', initials: 'PF', level: 4, xp: 712, location: 'Nairobi', avatar_color: 'yellow' },
      { index: 10, name: 'Boris Bar', initials: 'BB', level: 4, xp: 592, location: 'Boston', avatar_color: 'grey' },
      { index: 11, name: 'Olivia Baz', initials: 'OB', level: 4, xp: 420, location: 'Köln', avatar_color: 'teal' },
      { index: 12, name: 'Raj Singh', initials: 'RS', level: 3, xp: 333, location: 'Dublin', avatar_color: 'light-blue' },
      { index: 13, name: 'Tim Doh', initials: 'TD', level: 3, xp: 294, location: 'Buenos Aires', avatar_color: 'amber' },
      { index: 14, name: 'Louis Bon', initials: 'LB', level: 1, xp: 217, location: 'Las Vegas', avatar_color: 'brown' },
      { index: 15, name: 'Nico Paz', initials: 'NP', level: 2, xp: 17, location: 'Tokyo', avatar_color: 'pink' }
    ],
    winners: [
      { index: 1, name: 'Elli Vice', initials: 'EV', level: 7, xp: 2435, location: 'London', avatar_color: 'cyan' },
      { index: 2, name: 'Molnar Miller', initials: 'MM', level: 7, xp: 2143, location: 'Kairo', avatar_color: 'pink lighten-4' },
      { index: 3, name: 'Victor Yu', initials: 'VN', level: 7, xp: 1945, location: 'Honk Kong', avatar_color: 'blue-grey' }
    ]
  }),
  methods: {
  },
  computed: {}
}

</script>
<style scoped>
.space_second_place {
    background-color: silver;
    height: 300px;
    padding-top: 100px;
}

.space_first_place {
    background-color: gold;
    height: 400px;
    padding-top: 180px;
}

.space_third_place {
    background-color: chocolate;
    height: 200px;
    padding-top: 20px;
}
</style>
