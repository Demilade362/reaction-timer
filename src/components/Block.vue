<template>
  <div class="block" v-if="displayBlock" @click="stopTimer">Play</div>
  <div v-if="displayBlock">
    <button class="btn" @click="reset">Reset</button>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      displayBlock: null,
      displayText: null,
      timer: null,
      reactionTimer: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.displayBlock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTimer += 10;
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTimer);
      this.$emit('end', this.reactionTimer)
    },

    reset() {
      location.reload();
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 5px;
  background: crimson;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
