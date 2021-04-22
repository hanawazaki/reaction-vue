<template>
  <h1>Ninja Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="showResult" :skorAKhir="score" />
</template>

<script>
import Block from "./components/Block";
import Result from "./components/Result";

export default {
  name: "App",
  components: { Block, Result },

  data() {
    return {
      isPlaying: false,
      delay: null,
      showResult: false,
      score: null,
    };
  },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResult = false;
    },
    endGame(dataReactionTime) {
      this.score = dataReactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
