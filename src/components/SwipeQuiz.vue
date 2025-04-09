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

    <div class="card-container">
      <div v-if="currentIndex < cards.length" class="card">
        {{ cards[currentIndex].question }}
      </div>

      <div v-else class="completed-message">
        <p>Great Job</p>
        <button class="try-again" @click="restart">Try Again</button>
        <button class="next-btn">Next →</button>
      </div>
    </div>

    <div v-if="currentIndex < cards.length" class="actions">
      <button @click="handleSwipe('left')">← Physical Change</button>
      <button @click="handleSwipe('right')">Chemical Change →</button>
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
        { question: "Burning wood", correctDirection: "right" },
        { question: "Boiling water", correctDirection: "left" },
      ],
    };
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
  max-width: 500px;
  margin: auto;
  text-align: center;
  padding: 1rem;
  font-family: sans-serif;
  margin-bottom: 200px;
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
  margin-left: 5px;
  background: #cbd5e1;
  border-radius: 4px;
}

.progress-dots .active {
  background: #1e40af;
}

.instruction {
  margin: 1rem 0;
  font-size: 0.95rem;
  color: #334155;
}

.card-container {
  margin: 2rem 0;
}

.card {
  background: #f1f5f9;
  padding: 2rem;
  border-radius: 12px;
  font-size: 1.2rem;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.actions {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  margin-top: 2rem;
}

.actions button {
  flex: 1;
  padding: 1rem;
  font-size: 0.9rem;
  border: none;
  border-radius: 8px;
  background-color: #e2e8f0;
  cursor: pointer;
}

.actions button:hover {
  background-color: #cbd5e1;
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
</style>
