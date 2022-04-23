<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <button @click="start" :disabled="isPlaying">Play</button>
    <reaction-block v-if="isPlaying" :delay="delay" @clicked="clicked" />
    <result v-if="!isPlaying && !isFirstPlay" :reactionTime="reactionTime" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ReactionBlock from "./components/ReactionBlock.vue";
import Result from "./components/Result.vue";

export default defineComponent({
  name: "App",
  components: { ReactionBlock, Result },
  data() {
    return {
      isPlaying: false,
      isFirstPlay: true,
      delay: 0,
      reactionTime: 0,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.isFirstPlay = false;
    },
    clicked(time: number) {
      this.reactionTime = time;
      this.isPlaying = false;
    },
  },
});
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
  display: block;
  margin: 0 auto;
}
</style>
