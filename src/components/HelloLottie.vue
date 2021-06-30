<template>
  <h1>shapihuangdeshi</h1>
  <div class="container">
    <div v-for="(item, index) in DomRef" :key="index" :ref="setRef" />
  </div>
</template>
<script>
import { ref, onMounted } from "vue";
import lottie from "lottie-web";
import infinityLoading from "../assets/lottie-json/infinity-loading.json";
import loadingColourDots from "../assets/lottie-json/loading-colour-dots.json";
import onlineShopping from "../assets/lottie-json/online-shopping.json";
import sheep from "../assets/lottie-json/sheep.json";
import socket from "../assets/lottie-json/socket.json";
import wave from "../assets/lottie-json/wave.json";
export default {
  name: "HelloLottie",
  setup() {
    const DomRef = ref([
      infinityLoading,
      loadingColourDots,
      onlineShopping,
      sheep,
      socket,
      wave,
    ]);
    const myListRef = ref([]);
    const setRef = (el) => {
      myListRef.value.push(el);
    };

    const lottieMethod = () => {
      DomRef.value.forEach((element, index) => {
        lottie.loadAnimation({
          container: myListRef.value[index],
          renderer: "svg",
          loop: true,
          autoplay: true,
          animationData: element,
        });
      });
    };
    onMounted(() => {
      lottieMethod();
    });
    return {
      DomRef,
      setRef,
    };
  },
};
</script>
<style scoped>
h1 {
  margin: 100px 0;
  text-align: center;
}
.container {
  display: flex;
  justify-content: center;
}
.container div {
  flex: 1;
}
</style>
