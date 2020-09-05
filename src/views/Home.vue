<template>
  <div class="home">
    <CountDown />
  </div>
</template>

<script>
// @ is an alias to /src
import CountDown from "@/components/CountDown.vue";

export default {
  name: "Home",
  components: {
    CountDown
  }
};
</script>
