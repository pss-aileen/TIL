<script setup>
import Hero from "./components/Hero.vue";
import Navigation from "./components/Navigation.vue";
import Table from "./components/Table.vue";
import Footer from "./components/Footer.vue";
</script>

<template>
  <Navigation />
  <Hero />

  <div class="max-w-screen-lg mx-auto mt-12">
    <Table />
  </div>

  <Footer />
</template>

<style scoped></style>
