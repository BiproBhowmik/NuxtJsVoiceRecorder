<template>
  <div id="app">
    <h1>Simple Recorder.js demo</h1>
    <div id="controls">
      <button @click="startStopwatch" id="recordButton">Record</button>
      <button @click="isPaused = !isPaused" id="pauseButton" disabled>Pause</button>
      <button @click="stopStopWatch" id="stopButton" disabled>Stop</button>
    </div>
    <div id="formats">Format: start recording to see sample rate</div>
    <p><strong>Recordings for: {{hours}}:{{munites}}:{{seconds}} Unite of times</strong></p>
    <!-- <div id='seconds-counter'> </div>
    <button @click="startStopwatch">Click</button>
    <button @click="isPaused = !isPaused">Pause {{isPaused}} </button>
    <button @click="stopStopWatch">Stop </button> -->
    <ol id="recordingsList">

    </ol>
  </div>
</template>

<script lang="ts">

export default {
  data() {
    return {
      seconds: 0,
      miliSeconds: 0,
      munites: 0,
      hours: 0,
      isPaused: false,
      x: {},
    }
  },
  methods: {
  startStopwatch(){
    // setInterval(this.incrementSeconds, 1000);	//second counter
    this.x = setInterval(()=>{
      if (!this.isPaused) {
        if (this.seconds >= 60 ) {
          this.munites ++
          this.seconds = 0
        }
        if (this.munites >= 60) {
          this.hours ++
          this.munites = 0
          this.seconds = 0
        }
        this.seconds ++
        this.miliSeconds += 1000;
      }
    }, 1000);
  },
  stopStopWatch(){
    this.miliSeconds = 0
    this.seconds = 0
    this.munites = 0
    this.hours = 0
    this.isPaused = false
    clearInterval(this.x)
  },

  },
};
</script>