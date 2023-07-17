<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header
    class="header-nav | border-b border-b-zinc-950 | sticky top-0 | bg-white"
  >
    <div
      class="header-nav--wrapper | grid grid-cols-2 gap-4 grid-flow-row | xl:max-w-screen-xl 2xl:max-w-screen-2xl 3xl:max-w-screen-3xl mx-auto | ps-8 xl:px-16"
    >
      <div class="grid items-center">
        <img src="/images/Louis Keene Logo@2x.svg" alt="Louis Keene Logo" />
      </div>

      <div class="xl:grid hidden items-center justify-end">
        <nav class="flex items-center justify-stretch">
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

      <button
        class="flex xl:hidden justify-self-end self-center | hover:bg-zinc-500 hover:text-zinc-50 | transition-all duration-75 p-4"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="w-8 h-8"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M3.75 9h16.5m-16.5 6.75h16.5"
          />
        </svg>
      </button>
    </div>
  </header>
</template>

<style scoped lang="scss">
.header-nav--link {
  font-size: 1.5rem;
  font-weight: 700;
  color: theme("colors.zinc.700");
  text-align: center;
  min-width: 100px;
  padding: 16px 20px;

  box-shadow: inset 0 -2px 0 0px transparent;
  transition: all 0.2s ease-in-out;

  &:hover {
    color: theme("colors.zinc.950");
    box-shadow: inset 0 -2px 0 0px theme("colors.zinc.600");
  }
  &:focus {
    box-shadow: inset 0 -4px 0 0px theme("colors.zinc.950");
    color: theme("colors.zinc.600");
  }
}
</style>
