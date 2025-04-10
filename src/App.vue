<template>
  <div>
    <TapToReveal />
    <SwipeQuiz />
    <!-- <h1>Hello</h1> -->
  </div>
</template>

<script>
import TapToReveal from "./components/TapToReveal.vue";
import SwipeQuiz from "./components/SwipeQuiz.vue";

export default {
  components: {
    TapToReveal,
    SwipeQuiz,
  },
};
</script>
