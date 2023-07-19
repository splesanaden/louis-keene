<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header class="header-nav | border-y border-y-zinc-950 | bg-white | w-full">
    <div
      class="header-nav--wrapper | grid grid-cols-2 gap-4 grid-flow-row | w-screen h-full xl:max-w-screen-2xl 2xl:max-w-screen-2xl 3xl:max-w-screen-3xl | items-stretch | 2xl:mx-auto | ps-8 xl:pe-0 3xl:px-16"
    >
      <div class="grid items-center">
        <img src="./images/Louis Keene Logo@2x.svg" alt="Louis Keene Logo" />
      </div>

      <div class="xl:grid hidden items-stretch justify-end">
        <nav class="flex justify-stretch items-center">
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
  background-color: transparent;
  text-align: center;
  min-width: 100px;
  height: 100%;
  padding: 0 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 0px solid transparent;
  box-shadow: inset 0 -2px 0 0px transparent;
  transition: all 0.2s linear, box-shadow 0.075s linear;

  &:hover {
    color: theme("colors.zinc.950");
    box-shadow: inset 0 -3px 0 0px theme("colors.zinc.600");
    background-color: theme("colors.zinc.50");
  }
  &:focus,
  &.router-link-active {
    box-shadow: inset 0 -5px 0 0px theme("colors.zinc.950");
    color: white;
    background-color: theme("colors.zinc.950");
  }
  &:active {
    box-shadow: inset 0 0px 0px 0px transparent;
    color: white;
    background-color: theme("colors.zinc.700");
  }
}
</style>
