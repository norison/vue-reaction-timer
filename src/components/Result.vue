<template>
  <div class="result">
    <div class="title">Your result: {{ reactionTime }}</div>
    <div class="description">{{ description }}</div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Result",
  props: ["reactionTime"],
  data() {
    return {
      description: "",
    };
  },
  mounted() {
    if (this.reactionTime < 300) {
      this.description = "Awesom speed";
    } else if (this.reactionTime < 500) {
      this.description = "Normal speed";
    } else if (this.reactionTime < 800) {
      this.description = "Not bad speed";
    } else {
      this.description = "Low speed";
    }
  },
};
</script>

<style scoped>
.result {
  margin-top: 30px;
  font-size: 15px;
}
.description {
  margin-top: 5px;
  font-size: 20px;
  color: darkorchid;
}
</style>
