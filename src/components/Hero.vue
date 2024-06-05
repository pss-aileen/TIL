<script setup>
import Stats from "./Stats.vue";
</script>

<template>
  <div class="hero min-h-[80vh] bg-base-200">
    <div class="hero-content">
      <div class="">
        <div class="text-center">
          <h1 class="text-8xl font-extrabold">
            <span class="bg-clip-text text-transparent bg-gradient-to-r from-pink-500 via-violet-500 to-sky-500">
              Today I Learn.
            </span>
          </h1>
          <p class="py-6">Record my thoughts and memo, and study time. My memo is on GitHub.</p>
        </div>

        <Stats />
      </div>
    </div>
  </div>
</template>
