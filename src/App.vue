<script setup lang="ts">
import {SVGBelt, BeltProps, BeltSystem, ibjjfJSON, getRandomBelt} from 'svg-belt'

const ibjjfSystem: BeltSystem = new BeltSystem(ibjjfJSON);
const whiteBelt: BeltProps[] = ibjjfSystem.getBeltPropsByName("White", 0);

let randomSolid: BeltProps[] = getRandomBelt(
  true,
  false,
  0,
  "transition: all 1.0s ease-in-out;",
  ["Solid", "Striped", "Coral", "Split", "Checkered"],
  2000
);
</script>

<template>
  <SVGBelt class="logo" :belt-props="randomSolid" />
  <SVGBelt
        class="logo"
        :belt-props="
          ibjjfSystem.getBeltPropsAll('transition: all 0.5s ease-in-out;', 1000)
        "
      />
  <SVGBelt class="logo" :belt-props="whiteBelt"/>
  <h1>SVG-BELT Demo</h1>
</template>

<style scoped>
.logo {
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
