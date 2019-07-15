<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <CountDown />
  </div>
</template>

<script>
// @ is an alias to /src
import CountDown from "@/components/countdown.vue";

export default {
  name: "home",
  components: {
    CountDown
  }
};
</script>
