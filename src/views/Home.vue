<template>
  <div class="home">
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

<style scoped>
div.home {
  width: 100%;
  height: 100%;
}
</style>
