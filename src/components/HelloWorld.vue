<template>
  <v-container>
    <v-row class="text-center">

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          Multiplying Algebraic Terms
        </h1>

        <div>
          <video
          id="videoElement"
          width="800"
          height="600"
          src="../assets/teachingMultiplication.mp4"
          type="video/mp4"
          autoplay=false
          muted
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
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
    videoElement: null,
    paused: null
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
    }
  },
  computed: {
    playing () { return !this.paused }
  }
}
</script>
