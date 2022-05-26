<template>
  <h1>Reaction Timer Game</h1>
  <button class="btn" @click="start" :disabled="isPlaying">
    {{ btnText }}
  </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="result" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      btnText: "Start Game",
      score: null,
      result: false,
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.btnText = "Game Started";
      this.result = false;
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.result = true;
      this.btnText = "Start Game";
    },
  },
};
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

h1 {
  font-size: 2.5rem;
}

.btn {
  padding: 8px;
  color: white;
  background: crimson;
  font-size: 1.5rem;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  letter-spacing: 1px;
}


.btn[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
  color: white;
  margin-top: +5px;
}
</style>
