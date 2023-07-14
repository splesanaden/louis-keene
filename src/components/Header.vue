<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header class="header-nav | border-b border-b-zinc-950">
    <div
      class="header-nav--wrapper | grid grid-cols-2 gap-4 grid-flow-row | py-2 max-w-screen-xl mx-auto"
    >
      <div class="grid items-center">
        <img src="/images/Louis Keene Logo@2x.svg" alt="Louis Keene Logo" />
      </div>

      <div class="grid items-center justify-end">
        <nav class="flex items-center space-x-4">
          <router-link class="header-nav--link" to="/">Home</router-link>
          <router-link class="header-nav--link" to="/projects"
            >Projects</router-link
          >
          <router-link class="header-nav--link" to="/about"
            >About Me</router-link
          >
          <router-link class="header-nav--link" to="/contact"
            >Contact</router-link
          >
        </nav>
      </div>
    </div>
  </header>
</template>

<style scoped lang="scss">
.header-nav--link {
  font-size: 1.5rem;
  font-weight: 700;

  min-width: 100px;
  padding: 10px 20px;
  border-bottom: 2px solid transparent;
  transition: border-color 0.2s ease-in-out;
  &:hover {
    border-bottom: 2px solid theme("colors.zinc.950");
  }
}
</style>
