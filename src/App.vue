<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Capitalize from './components/Capitalizer.vue'
</script>

<template>
  <header>
    <h1>The Capitalizer</h1>
  </header>
  <Capitalize />
</template>

<style>
:root {
  --colors-darkblue: #313a4f;
  --colors-light: #f6f7f9;
  --colors-white: #fcfcfc;
  --colors-red: #ff7070;
  --colors-lightred: #ffcccc;
  --colors-blue: #4f5e7f;
  --colors-lightblue: #d1d6e0;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  background-color: var(--colors-light);
  color: var(--colors-darkblue);
  font-family: Poppins, sans-serif;
  font-size: 1rem;
  font-size: clamp(1rem, 0.95rem + 0.25vw, 1.25rem);
}

header {
  padding: 1rem;
  background-color: var(--colors-darkblue);
  color: var(--colors-white);
  display: grid;
  grid-template-columns: 1fr minmax(min-content, 1024px) 1fr;
}

h1 {
  grid-column: 2;
}
</style>