<template>
  <div class="relative h-screen overflow-hidden">
    <header>
      <title>Parallax Effect</title>
    </header>

    <img
      ref="background"
      src="~/assets/background.png"
      class="absolute top-0 left-0 w-full"
    />
    <img
      ref="midground"
      src="~/assets/midground.png"
      class="absolute top-0 left-0 w-full"
    />

    <div
      class="absolute top-0 left-0 w-full flex justify-center items-center h-screen"
    >
      <div
        class="bg-black opacity-20 absolute top-0 left-0 w-full h-full"
      ></div>

      <div
        class="flex flex-col items-center space-y-5 text-white drop-shadow-2xl opacity-90"
        ref="text"
      >
        <h1 class="font-bold text-8xl">창덕궁</h1>
        <h3 class="text-xl">고요한 아침의 궁궐</h3>
      </div>
    </div>

    <img
      ref="foreground"
      src="~/assets/foreground.png"
      class="absolute top-0 left-0 w-full"
    />
  </div>
  <div class="h-screen flex justify-center items-center bg-zinc-950">
    <h1 class="text-4xl text-white font-bold">@suhjae.dev</h1>
  </div>
</template>

<script setup>
import { onMounted, onBeforeUnmount, ref } from "vue";

const background = ref(null);
const midground = ref(null);
const foreground = ref(null);
const text = ref(null);

let ticking = false;

const handleScroll = () => {
  if (!ticking) {
    window.requestAnimationFrame(() => {
      const scrollY = window.scrollY;
      if (background.value)
        background.value.style.transform = `translateY(${scrollY}px)`;
      if (midground.value)
        midground.value.style.transform = `translateY(${scrollY * 0.7}px)`;
      if (foreground.value)
        foreground.value.style.transform = `translateY(${scrollY * 0.3}px)`;
      if (text.value)
        text.value.style.transform = `translateY(${scrollY * 0.5}px)`;
      ticking = false;
    });
    ticking = true;
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style>
body {
  margin: 0;
  overflow-x: hidden;
}
</style>
