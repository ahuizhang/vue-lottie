<template>
  <div class="container">
    <div ref="infinityLoading"></div>
    <div ref="loadingColourDots"></div>
    <div ref="onlineShopping"></div>
    <div ref="sheep"></div>
    <div ref="socket"></div>
    <div ref="wave"></div>
  </div>
</template>

<script>
import lottie from "lottie-web";
import infinityLoading from "../assets/infinity-loading.json";
import loadingColourDots from "../assets/loading-colour-dots.json";
import onlineShopping from "../assets/online-shopping.json";
import sheep from "../assets/sheep.json";
import socket from "../assets/socket.json";
import wave from "../assets/wave.json";
export default {
  name: "HelloWorld",
  data() {
    return {
      allJson: {
        infinityLoading,
        loadingColourDots,
        onlineShopping,
        sheep,
        socket,
        wave,
      },
    };
  },
  mounted() {
    for (const key in this.allJson) {
      if (Object.hasOwnProperty.call(this.allJson, key)) {
        const element = this.allJson[key];
        lottie.loadAnimation({
          container: this.$refs[key],
          renderer: "svg",
          loop: true,
          autoplay: true,
          animationData: element,
        });
      }
    }
  },
};
</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
}
.container div {
  flex: 1;
}
</style>
