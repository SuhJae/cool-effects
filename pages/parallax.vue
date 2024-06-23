<template>
  <ParallaxContainer>
    <ParallaxLayer src="/images/background.png" :multiplier="1" />
    <ParallaxLayer src="/images/midground.png" :multiplier="0.7" />
    <ParallaxLayer :multiplier="0.5">
      <div class="titleBase">
        <h1 class="title font-bold text-8xl">창덕궁</h1>
        <h3 class="subtitle text-xl">고요한 아침의 궁궐</h3>
      </div>
    </ParallaxLayer>
    <ParallaxLayer src="/images/foreground.png" :multiplier="0.3" />
  </ParallaxContainer>

  <div class="h-screen bg-zinc-950 flex flex-col justify-center items-center">
    <h3 class="text-white text-center text-2xl py-8">@suhjae.dev</h3>
  </div>
</template>

<style scoped>
/*  */
</style>