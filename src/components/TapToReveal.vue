<template>
  <div class="card-container">
    <div
      v-for="(card, index) in cards"
      :key="index"
      class="card"
      :class="{ flipped: card.revealed }"
      @click="revealCard(index)"
    >
      <div class="front">
        <div class="inner">
          <img :src="card.imageQue" alt="img" width="20px" />
          <p>{{ card.question }}</p>
        </div>
      </div>
      <div class="back">
        <div class="inner">
          <img :src="card.image" alt="img" width="20px" />
          <p>{{ card.answer }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cards: [
        {
          question:
            "What is the utils needed to connect ur phone to an headset?",
          answer: "Bluetooth",
          revealed: false,
          image: "/bluetooth.svg",
          imageQue: "/seal-question.svg",
        },
        {
          question: "Capital of France?",
          answer: "Paris",
          revealed: false,
          image: "/activity.svg",
          imageQue: "/seal-question.svg",
        },
        {
          question: "Capital of France?",
          answer: "Paris",
          revealed: false,
          image: "/activity.svg",
          imageQue: "/seal-question.svg",
        },
        {
          question: "Capital of France?",
          answer: "Paris",
          revealed: false,
          image: "/activity.svg",
          imageQue: "/seal-question.svg",
        },
      ],
    };
  },
  methods: {
    revealCard(index) {
      this.cards[index].revealed = !this.cards[index].revealed;
    },
  },
};
</script>

<style scoped>
.card-container {
  display: grid;
  grid-template-columns: repeat(2, auto);
  justify-content: center;
  column-gap: 1rem;
  row-gap: 1rem;
  width: 100%;
  /* margin: 0 auto; */
}

.card {
  width: 250px;
  height: 250px;
  perspective: 1000px;
  cursor: pointer;
  position: relative;
}

.card .front,
.card .back {
  width: 100%;
  height: 100%;
  background-color: aqua;
  border-radius: 20px;
  backface-visibility: hidden;
  transition: transform 0.6s;
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
}
.inner {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.inner p {
  text-align: center;
}

.card .back {
  transform: rotateY(180deg);
}

.card.flipped .front {
  transform: rotateY(180deg);
}

.card.flipped .back {
  transform: rotateY(360deg);
}

@media (max-width: 750px) {
  .card-container {
    grid-template-columns: 1fr;
    margin-left: 60px;
    margin-top: 10px;
  }
}
</style>
