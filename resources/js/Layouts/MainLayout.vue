<script setup lang="ts">
import Navbar from '../Components/Navbar.vue';
</script>

<template>
  <Navbar></Navbar>
  <main class="container mx-auto mt-8 p-6" scroll-region>
    <slot></slot>
  </main>
</template>
