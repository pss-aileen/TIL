<script setup>
import { ref } from "vue";
import studyLog2024 from "./../database/studyLog2024.json";

const today = new Date();
const thisYear = today.getFullYear();
const thisMonth = (today.getMonth() + 1).toString().padStart(2, "0");
const thisDate = (today.getDate() + 1).toString().padStart(2, "0");

const newArray = [];

for (const data of studyLog2024) {
  const [year, month, day] = data.date.split("-");
  // console.log(data.date);
  let totalTimeOneDay = 0;
  for (const task of data.tasks) {
    totalTimeOneDay += task.time;
  }

  if (data.date === `${thisYear}-${thisMonth}-${thisDate}`) {
    console.log(`${thisYear}-${thisMonth}-${thisDate}`);
    break;
  }
  newArray.push({
    date: data.date,
    time: totalTimeOneDay,
    memo: data.memo.join(" / "),
  });
}

console.log(newArray);
const reversedArray = newArray.reverse();
const logs = ref(reversedArray);
</script>

<template>
  <div class="overflow-x-auto mt-12">
    <table class="table">
      <!-- head -->
      <thead>
        <tr>
          <th>Date</th>
          <th>Study Time</th>
          <th class="w-2/3">Memo</th>
        </tr>
      </thead>
      <tbody v-for="(log, index) in logs">
        <tr>
          <td>{{ log.date }}</td>
          <td :class="log.time >= 3 ? 'text-primary' : ''">{{ log.time }}h</td>
          <td>{{ log.memo }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
