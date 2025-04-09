<template>
  <div class="app">
    <TapToReveal />
    <SwipeQuiz />
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
