<template>
  <h1>Reaction Game</h1>
  <div @click="start" class="btn-start" :class="{ disableButton: isPlaying }">
    <strong>Let's Start</strong>
  </div>

  <Block v-if="isPlaying" :delay="delay" @end="resultGame" />
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    resultGame(reactionTime) {
      this.score = reactionTime;
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
  color: #2d3436;
  margin-top: 60px;
}
.btn-start {
  width: 100px;
  background: #636e72;
  color: white;
  text-align: center;
  border-radius: 5px;
  text-align: center;
  padding: 10px;
  margin: 10px auto;
  cursor: pointer;
}
.disableButton {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
