<script setup>
import { ref } from "vue";
import studyLog2023 from "./../database/studyLog2023.json";
import studyLog2024 from "./../database/studyLog2024.json";

// console.log(studyLog);

const specifiedDate = new Date("2023-11-18");
const today = new Date();
const thisMonth = today.getMonth() + 1;
// console.log(thisMonth);

const diffTime = Math.abs(today - specifiedDate);
const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

let totalTime = 0;
let monthlyTotalTime = 0;

for (const data of studyLog2023) {
  for (const task of data.tasks) {
    totalTime += task.time;
  }
}

for (const data of studyLog2024) {
  const [year, month, day] = data.date.split("-");
  if (Number(month) === thisMonth) {
    for (const task of data.tasks) {
      monthlyTotalTime += task.time;
    }
  }
  for (const task of data.tasks) {
    totalTime += task.time;
  }
}

const monthlyTotalTimeForShow = ref(monthlyTotalTime);
const totalTimeForShow = ref(totalTime);
const diffDaysForShow = ref(diffDays);
</script>

<template>
  <div class="mt-8 flex justify-center">
    <div class="stats shadow">
      <div class="stat place-items-center">
        <div class="stat-title">Study Time</div>
        <div class="stat-value">{{ monthlyTotalTimeForShow }}h</div>
        <div class="stat-desc">June, 2024</div>
      </div>
      <div class="stat place-items-center">
        <div class="stat-title">Study Time</div>
        <div class="stat-value">{{ totalTimeForShow }}h</div>
        <div class="stat-desc">From 18 Nov, 2023 to Today</div>
      </div>
      <div class="stat place-items-center">
        <div class="stat-title">Days</div>
        <div class="stat-value">{{ diffDays }}days</div>
        <div class="stat-desc">From 18 Nov, 2023 to Today</div>
      </div>
    </div>
  </div>
</template>
