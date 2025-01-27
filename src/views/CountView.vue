<script setup>
import { useCounterStore } from '../stores/counter.js'
const counterRef = useCounterStore()
</script>

<template>
  <main class="counter-container">
    <h1 class="title">Vue Counter App</h1>
    <div class="counter-buttons">
      <button @click="counterRef.increment" class="counter-btn increment-btn">Plus</button>
      <button @click="counterRef.decrement" class="counter-btn decrement-btn">Minus</button>
    </div>
    <div class="counter-display">
      <h2 class="count">
        Count: <span>{{ counterRef.count }}</span>
      </h2>
      <h2 class="double-count">
        Doubled Count: <span>{{ counterRef.doubleCount }}</span>
      </h2>
    </div>
  </main>
</template>

<style scoped>
.counter-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #f3f4f6;
  font-family: 'Arial', sans-serif;
  text-align: center;
}

.title {
  font-size: 28px;
  font-weight: bold;
  color: #4f4f4f;
  margin-bottom: 30px;
}

.counter-buttons {
  margin-bottom: 20px;
}

.counter-btn {
  padding: 15px 25px;
  font-size: 18px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  margin: 0 10px;
  transition:
    transform 0.3s,
    background-color 0.3s;
}

.increment-btn {
  background-color: #4caf50;
  color: white;
}

.increment-btn:hover {
  background-color: #45a049;
  transform: translateY(-3px);
}

.decrement-btn {
  background-color: #f44336;
  color: white;
}

.decrement-btn:hover {
  background-color: #e53935;
  transform: translateY(-3px);
}

.counter-display {
  margin-top: 20px;
}

.count,
.double-count {
  font-size: 22px;
  color: #333;
}

span {
  font-weight: bold;
  font-size: 24px;
}
</style>
