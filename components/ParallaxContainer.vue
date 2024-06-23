<template>
  <div class="parallax-container">
    <slot></slot>
  </div>
</template>

<script setup></script>

<style scoped>
.parallax-container {
  position: relative;
  height: 100vh;
  overflow: hidden;
}
</style>
