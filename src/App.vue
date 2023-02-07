<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block class="block" v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <Results v-if="showResult" :score="score"></Results>

</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue"
export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      showResult: false,
      score: null
    }
  },
  methods: {
    start() {
      this.delay = 1000 + Math.random() * 3000
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.showResult = true;
      this.score = reactionTime;
      this.isPlaying = false;
    }
  },

}
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
  background-color: rgb(21, 154, 110);
  color:wheat;
  border: none;
  padding: 8px 16px;
  border-radius: 10px;
  font-size: 25px;
  font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', sans-serif;
  letter-spacing: 2px;
  font-weight: bold;
  margin: 10px;
  height: 70px;
  width: 180px;
  cursor: pointer;
}

[disabled] {
  opacity: 0.5;
  cursor: not-allowed;

}
</style>
