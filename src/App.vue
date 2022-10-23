<template>
 <div>
  <h1>Ninja Reaction Timer</h1>
  <button @click="handlePlayButton" :disabled="isPlaying"> Play! </button>
 </div>
 <Block v-if="isPlaying" :delay="delay" />
</template>

<script>
import Block from './components/Block.vue'

export default {
  name: 'App',
  components: {
    Block
  },
  methods: {
    handlePlayButton() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 3000
      console.log(this.delay)
    }
  },
  data() {
    return {
      isPlaying: false,
      delay: null

    }
  } 
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
</style>
