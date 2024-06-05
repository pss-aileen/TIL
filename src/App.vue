<script setup>
import Hero from "./components/Hero.vue";
import Navigation from "./components/Navigation.vue";
</script>

<template>
  <Navigation />
  <Hero />

  <div class="max-w-screen-lg mx-auto mt-12">
    <div class="overflow-x-auto mt-12">
      <table class="table">
        <!-- head -->
        <thead>
          <tr>
            <th>Date</th>
            <th>Study Time</th>
            <th>Done</th>
          </tr>
        </thead>
        <tbody>
          <tr class="bg-base-200">
            <td>2024/06/05</td>
            <td>0.5h</td>
            <td>Programming: 〜〜〜、English: 〜〜</td>
          </tr>
          <tr>
            <td>2024/06/05</td>
            <td>0.5h</td>
            <td>Programming: 〜〜〜、English: 〜〜</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <footer class="footer footer-center p-4 bg-base-300 text-base-content mt-12">
    <aside>
      <p>Copyright © 2024 - All right reserved by Aileen TIL</p>
    </aside>
  </footer>
</template>

<style scoped></style>
