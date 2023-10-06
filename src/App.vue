<template>
  <div class="flex flex-center">
    <div class="quote-container">
      <transition name="slide-fade" mode="out-in">
        <div :key="currentQuoteIndex" class="quote">
          {{ quotes[currentQuoteIndex] }}<br />
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
import quotes from './complimenten.json';

export default {
  data() {
    return {
      currentQuoteIndex: 0,
      quotes,
    };
  },
  mounted() {
    setInterval(() => {
      if (this.currentQuoteIndex < this.quotes.length - 1) {
        this.currentQuoteIndex++;
      } else {
        this.currentQuoteIndex = 0;
      }
    }, 30000);
  },
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Red+Hat+Display&display=swap');

.flex {
  width: 100vw;
  height: 100vh;
  display: flex;
  background-color: #025464;
}

.flex-center {
  align-items: center;
  justify-content: center;
}

.quote-container {
  color: white;
  overflow: hidden;
  font-family: 'Red Hat Display', sans-serif;
}

.quote {
  padding: 20px;
  font-size: 48px;
  text-align: center;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 1s ease;
}
.slide-fade-enter, 
.slide-fade-leave-to /* .slide-fade-leave-active in <2.1.8 */ {
  transform: translateX(100%);
  opacity: 0;
}
</style>
