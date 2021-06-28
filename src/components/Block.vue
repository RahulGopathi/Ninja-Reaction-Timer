<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      timer: null,
      reationTime: null,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  props: ["delay"],
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reationTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reationTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0px;
  margin: 40px auto;
}
</style>