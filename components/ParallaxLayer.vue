<template>
  <div
    :class="['parallax-layer', { 'is-image': isImage }]"
    :style="{
      transform: `translateY(${scrollY * multiplier}px)`,
      backgroundImage: isImage ? `url(${src})` : '',
    }"
  >
    <slot v-if="!isImage"></slot>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from "vue";

const props = defineProps({
  src: {
    type: String,
    default: "",
  },
  multiplier: {
    type: Number,
    required: true,
  },
});

const isImage = ref(!!props.src);
const scrollY = ref(0);
let ticking = false;

const handleScroll = () => {
  if (!ticking) {
    window.requestAnimationFrame(() => {
      scrollY.value = window.scrollY;
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

watch(
  () => props.src,
  (newVal) => {
    isImage.value = !!newVal;
  }
);
</script>

<style scoped>
.parallax-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.is-image {
  background-size: cover;
  background-position: center;
}
</style>
