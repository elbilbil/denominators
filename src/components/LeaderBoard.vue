<template>
  <v-container>
      <v-row>
          <h1>Leaderboard</h1>
      </v-row>
      <v-row>
          <v-col cols="8">
              <v-card outlined>
                  <v-spacer></v-spacer>
                  <v-row class="text-center">
                      <v-col class="mt-2" cols="4">2
                      </v-col>
                      <v-col cols="4">1</v-col>
                      <v-col class="mt-2" cols="4">3</v-col>
                  </v-row>
              </v-card>
          </v-col>
          <v-col cols="4">
              <v-card outlined>
                <v-simple-table class="ma-2">
                    <template v-slot:default>
                    <thead>
                        <tr>
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
      { name: 'John Doe', initials: 'JD', level: 6, xp: 1337, location: 'Bangalore', avatar_color: 'red' },
      { name: 'Jim Smith', initials: 'JS', level: 7, xp: 1276, location: 'Sidney', avatar_color: 'blue' },
      { name: 'Lara Wood', initials: 'LW', level: 6, xp: 1156, location: 'Paris', avatar_color: 'orange' },
      { name: 'Laura Test', initials: 'LT', level: 5, xp: 928, location: 'London', avatar_color: 'green' },
      { name: 'Nik Lou', initials: 'NL', level: 5, xp: 911, location: 'Hanoi', avatar_color: 'purple' },
      { name: 'Ying Xie', initials: 'YX', level: 6, xp: 834, location: 'New York', avatar_color: 'lime' },
      { name: 'Pete Foo', initials: 'PF', level: 4, xp: 712, location: 'Nairobi', avatar_color: 'yellow' },
      { name: 'Boris Bar', initials: 'BB', level: 4, xp: 592, location: 'Boston', avatar_color: 'grey' },
      { name: 'Olivia Baz', initials: 'OB', level: 4, xp: 420, location: 'Köln', avatar_color: 'teal' },
      { name: 'Rajesh Singh', initials: 'RS', level: 3, xp: 333, location: 'Dublin', avatar_color: 'light-blue' },
      { name: 'Tim R. Miller', initials: 'TM', level: 3, xp: 294, location: 'Buenos Aires', avatar_color: 'amber' },
      { name: 'Louis Charles', initials: 'LC', level: 1, xp: 217, location: 'Las Vegas', avatar_color: 'brown' },
      { name: 'Ignazio Paz', initials: 'IP', level: 2, xp: 17, location: 'Tokyo', avatar_color: 'pink' }
    ]
  }),
  methods: {
  },
  computed: {}
}

</script>
