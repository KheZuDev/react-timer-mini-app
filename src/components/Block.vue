<template>
  <div class="Click" v-if="showBlock" @click="stopTimer">
    CLick here{{ delay }}
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      score: 0,
      timer: null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.score += 50;
      }, 50);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.score);
    },
  },
};
</script>

<style>
.Click {
  height: 150px;
  width: 180px;
  border-radius: 50%;
  margin: 20px auto;
  padding-top: 30px;
  background-color: aqua;
}
</style>