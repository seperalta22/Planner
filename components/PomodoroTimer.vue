<script lang="ts" setup>

import { ref } from 'vue'

const timer = ref(0)
const pomodoroTime = 25 * 60 * 1000
let interval: any = null

const startTimer = () => {
  timer.value = pomodoroTime
  interval = setInterval(() => {
    timer.value -= 1000
    if (timer.value <= 0) {
      clearInterval(interval)
    }
  }, 1000)
}

const stopTimer = () => {
  clearInterval(interval)
  timer.value = 0
}

const pauseTimer = () => {
  clearInterval(interval)
}

const resetTimer = () => {
  clearInterval(interval)
  timer.value = 0
  startTimer()
}

</script>
<template>
  <div>
    <button @click="startTimer">Start Pomodoro</button>
    <button @click="stopTimer">Stop Pomodoro</button>
    <button @click="pauseTimer">Pause Pomodoro</button>
    <button @click="resetTimer">Reset Pomodoro</button>
    <p>{{ timer }}</p>
  </div>
</template>
    
 




