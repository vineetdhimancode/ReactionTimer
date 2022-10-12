<template>
  <h1>Reaction Timer</h1>
  <button :class="{'disabledPlayBtn': isPlaying, 'playBtn': true}" :disabled="isPlaying" @click="start">Play</button>
  <Block v-if="isPlaying" :delay="delay" @showResult="showResult"></Block>
  <Result v-if="displayResult" :reactionTime="score"/>
</template>

<script>
import Block from '@/components/Block.vue';
import Result from '@/components/Result.vue';
export default {
  name: "App",
  components: {
    Result,
    Block,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      displayResult: false,
      score: 0
    };
  },
  methods: {
    start() {
      this.isPlaying = !this.isPlaying;
      this.displayResult = false;
      this.delay = 2000 + Math.random() * 5000
    },
    showResult(time) {
      this.isPlaying = false;
      this.displayResult = true;
      this.score = time
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.playBtn {
  padding: 10px 20px;
  color: white;
  background: rgb(224, 70, 70);
  border: none;
  border-radius: 10px;
  cursor: pointer;
}

.playBtn:focus {
  background: rgb(145, 43, 43);
  cursor: pointer;
}

.disabledPlayBtn {
  background: rgb(224 167 167);
}
</style>
