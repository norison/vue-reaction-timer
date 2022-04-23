<template>
  <div class="block" v-if="showBlock" @click="onClick">Click me</div>
</template>

<script lang="ts">
export default {
  name: "ReactionBlock",
  props: ["delay", "clicked"],
  data() {
    return {
      showBlock: false,
      startDate: Date,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startDate = new Date();
    }, this.delay);
  },
  methods: {
    onClick() {
      const time = new Date().getTime() - this.startDate.getTime();
      this.$emit("clicked", time);
    },
  },
};
</script>

<style>
.block {
  margin: 30px auto;
  width: 300px;
  height: 200px;
  background-color: black;
  color: white;
  border-radius: 6%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
