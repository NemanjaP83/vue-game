<template>
  <div class="wrapper">
    <h1>Reaction Timer App</h1>
    <button class="play-btn" @click="start" :class="{disabled: isPlaying === true}">play</button>
    <Block v-if="isPlaying" :delay="delay" @endGame="endGame" />
    <Result v-if="showResults" :reactionTime="reactionTime" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: 0,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 4000,
      this.isPlaying = true,
      this.showResults = false
    },
    endGame(score) {
      this.reactionTime = score,
      this.isPlaying = false,
      this.showResults = true
    }
  }
}
</script>

<style>
  .wrapper {
    width: 100%;
    height: 300px;
  }
  .play-btn {
    margin: 20px 0 30px;
    padding: 10px 18px;
    background-color: crimson;
    font-size: 16px;
    color: white;
    outline: none;
    border: none;
    border-radius: 3px;
    cursor: pointer;
  }
  .disabled {
    background-color: darkgray;
    cursor: not-allowed;
  }
</style>
