<template>
  <div class="quiz-wrapper">
    <div class="lesson-header">
      <p>Lesson 3.1</p>
      <div class="progress-dots">
        <span
          v-for="i in cards.length"
          :key="i"
          :class="{ active: i <= currentIndex }"
        />
      </div>
    </div>

    <p class="instruction">
      Tap the arrows below the cards to swipe the cards in the direction of the
      correct change.
    </p>

    <div class="swipe-labels">
      <span>← Physical Change</span>
      <span>Chemical Change →</span>
    </div>

    <div class="card-swipe-area">
      <button class="arrow left" @click="handleSwipe('left')">←</button>

      <div class="card-stack">
        <div
          v-for="(card, index) in visibleCards"
          :key="index"
          class="card"
          :style="{ zIndex: cards.length - index }"
        >
          <div class="icon">🔥</div>
          <p>{{ card.question }}</p>
        </div>
      </div>

      <button class="arrow right" @click="handleSwipe('right')">→</button>
    </div>

    <div v-if="currentIndex >= cards.length" class="completed-message">
      <p>Great Job</p>
      <button class="try-again" @click="restart">Try Again</button>
      <button class="next-btn">Next →</button>
    </div>

    <div v-if="showTryAgain" class="try-again-message">
      <p>Wrong Answer!</p>
      <button @click="showTryAgain = false">Try Again</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      showTryAgain: false,
      cards: [
        { question: "Melting ice", correctDirection: "left" },
        { question: "Burning paper", correctDirection: "right" },
        { question: "Boiling water", correctDirection: "left" },
      ],
    };
  },
  computed: {
    visibleCards() {
      return this.cards.slice(this.currentIndex);
    },
  },
  methods: {
    handleSwipe(direction) {
      if (this.cards[this.currentIndex].correctDirection === direction) {
        this.currentIndex++;
      } else {
        this.showTryAgain = true;
      }
    },
    restart() {
      this.currentIndex = 0;
      this.showTryAgain = false;
    },
  },
};
</script>

<style scoped>
.quiz-wrapper {
  max-width: 600px;
  margin: auto;
  text-align: center;
  font-family: "Segoe UI", sans-serif;
  padding: 2rem 1rem;
  margin-bottom: 250px;
  align-items: center;
}

.lesson-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: bold;
}

.progress-dots span {
  display: inline-block;
  width: 12px;
  height: 4px;
  margin-left: 4px;
  background: #cbd5e1;
  border-radius: 4px;
}
.progress-dots .active {
  background: #1e40af;
}

.instruction {
  font-size: 0.95rem;
  color: #334155;
  margin: 1rem 0;
}

.swipe-labels {
  display: flex;
  justify-content: space-between;
  margin: 0.5rem 0 0.2rem;
  font-size: 0.85rem;
  color: #475569;
}

.card-swipe-area {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  margin: 1rem 0 2rem;
}

.arrow {
  background-color: #e2e8f0;
  border: none;
  border-radius: 8px;
  font-size: 1.5rem;
  padding: 0.5rem 1rem;
  cursor: pointer;
  color: #1e293b;
}
.arrow:hover {
  background-color: #cbd5e1;
}

.card-stack {
  position: relative;
  width: 220px;
  height: 300px;
  margin: 0 1.5rem;
  justify-content: center;
  margin-right: 70px;
}
.card {
  background: linear-gradient(to bottom right, #38bdf8, #06b6d4);
  color: white;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  transition: transform 0.3s ease;
}

.card .icon {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.completed-message {
  margin-top: 2rem;
}

.completed-message p {
  font-size: 1.5rem;
  font-weight: bold;
  color: green;
  margin-bottom: 1rem;
}

.try-again,
.next-btn {
  margin: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  border: 1px solid #ccc;
  background-color: white;
  cursor: pointer;
}

.next-btn {
  background-color: #1d4ed8;
  color: white;
  border: none;
}

.try-again-message {
  margin-top: 1rem;
  background: #fee2e2;
  padding: 1rem;
  border-radius: 8px;
  color: #b91c1c;
}

@media (max-width: 600px) {
  .card {
    padding: 3px;
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
    position: absolute;
    top: 0;
    left: 0;
    width: 80%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: transform 0.3s ease;
  }
  .progress-dots span {
    width: 4px;
    height: 4px;
    margin-left: 8px;
    background: #cbd5e1;
    border-radius: 4px;
  }
}
</style>
