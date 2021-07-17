<template>
  <v-container>
    <v-alert
    type="success"
    transition="fade-transition"
    :value="alert"
    >
    Excellent! You have gained <strong>+50</strong> XP
    </v-alert>
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
                controls
                src="../assets/teachingMultiplication.mp4"
                type="video/mp4"
                autoplay="false"
                muted
                width="100%"
                ></video>
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

    <v-dialog
      v-model="dialog"
      persistent
      max-width="290"
    >
      <v-card>
        <v-card-title>
          Almost. Learn why your answer was wrong:
        </v-card-title>
        <video
          id="videoElement"
          src="../assets/explanation.mp4"
          type="video/mp4"
          autoplay="false"
          width="100%"
          @canplay="updatePaused" @playing="updatePaused" @pause="updatePaused">
        </video>
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
        <v-card-actions>
          <v-btn
            color="red darken-1"
            text
            @click="closeModal()"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    alert: false,
    dialog: false,
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
      this.videoElement.play()
    },
    pause () {
      this.videoElement.pause()
    },
    evaluateAnswer (input) {
      if (input) {
        this.showAlert()
      } else {
        this.dialog = true
      }
    },
    closeModal () {
      this.dialog = false
      this.videoElement.pause()
    },
    showAlert () {
      this.alert = true
      window.setInterval(() => {
        this.alert = false
      }, 3000) // visible for 3 seconds, then hidden again
    }
  },
  computed: {
    playing () { return !this.paused }
  }
}
</script>
