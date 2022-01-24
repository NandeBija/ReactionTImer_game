<template>
  <div class="block" v-if="showBlock" @click="stopTimer">click me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  //  for timer
  mounted() {
    console.log("mounted");
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
  //  displays when the block is shown life cyccycle hooks
  //    updated(){
  // console.log('ive arrived')
  //    },
  //    unmounted(){
  //      console.log('Nothing here')
  //    }
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: pink;
  color: white;
  text-align: center;
  padding: 40px 0;
  margin: 40px auto;
}
button {
  background-color: pink;
  color: white;
  border-radius: 6px;
  width: 50px;
  height: 30px;
}
button[disabled] {
  opacity: 0;
}
</style>
