<template>
  <v-container>
    <v-row class="text-center">

      <v-col class="mb-4">
        <v-row>
          <v-col cols="8">
            <v-card outlined>
              <v-col offset="1" cols="10">
                <v-progress-linear value="28" color="green"></v-progress-linear>
              </v-col>
              <h2 class="mb-3">
                Multiplying Algebraic Terms
              </h2>
              <div>
                <video
                id="videoElement"
                src="../assets/teachingMultiplication.mp4"
                type="video/mp4"
                autoplay=false
                muted
                width="100%"
                @canplay="updatePaused" @playing="updatePaused" @pause="updatePaused"></video>
                <div class="controls text-left">
                  <v-btn v-show="paused" @click="play" text icon>
                        <v-icon
                          large
                        >
                          mdi-play
                        </v-icon>
                  </v-btn>
                  <v-btn v-show="playing" @click="pause" text icon>
                        <v-icon
                          large
                        >
                          mdi-pause
                        </v-icon>
                  </v-btn>
                </div>
              </div>
            </v-card>
          </v-col>

          <v-col cols="4">
          <v-card
            class="mx-auto"
            outlined
          >
            <v-list-item three-line>
              <v-list-item-content>
                <div class="text-overline mb-4">
                  LEVEL 1
                </div>
                <v-list-item-title class="text-h5 mb-1">
                  Simplify 5x<sup>2</sup> * 2x<sup>3</sup>
                </v-list-item-title>
                <v-list-item-subtitle>
                  <v-radio-group class="ml-2" v-model="radioGroup">
                    <v-radio
                      v-for="n in answers"
                      :key="n.id"
                      :label="n.text"
                      :value="n.id"
                      @click="evaluateAnswer(n.correct)"
                    ></v-radio>
                  </v-radio-group>
                </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-card>
          </v-col>
        </v-row>
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    videoElement: null,
    paused: null,
    answers: [
      { id: 1, text: '5x^5', correct: false },
      { id: 2, text: '10x^5', correct: true },
      { id: 3, text: '10x^6', correct: false },
      { id: 4, text: 'Cannot be simplified', correct: false }
    ]
  }),
  methods: {
    updatePaused (event) {
      this.videoElement = event.target
      this.paused = event.target.paused
    },
    play () {
      console.log('PLAY')
      this.videoElement.play()
    },
    pause () {
      console.log('PAUSE')
      this.videoElement.pause()
    },
    evaluateAnswer (input) {
      if (input) {
        console.log('CORRECT')
      } else {
        console.log('FALSE')
      }
    }
  },
  computed: {
    playing () { return !this.paused }
  }
}
</script>
