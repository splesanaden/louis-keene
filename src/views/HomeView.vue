<script setup></script>

<template>
  <main
    class="xl:max-w-screen-xl 2xl:max-w-screen-2xl 3xl:max-w-screen-3xl | mx-auto p-8 xl:p-16"
  >
    <div
      class="grid grid-cols-2 xl:grid-cols-3 xl:grid-rows-2 gap-2 xl:gap-8 grid-flow-row-dense"
    >
      <div class="content-item | col-span-1 row-span-1 xl:order-1">
        <img src="/images/portfolio/home/home-1.webp" alt="Hero Image" />
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-2">
        <img src="/images/portfolio/home/home-2.webp" alt="Hero Image" />
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-3">
        <img src="/images/portfolio/home/home-3.webp" alt="Hero Image" />
      </div>
      <div
        class="content-item | col-span-2 xl:col-span-1 row-span-1 | flex flex-col align-center justify-center | order-first xl:order-4"
      >
        <h1 class="text-3xl 2xl:text-4xl font-bold | mb-8">
          Build a Better Home.
        </h1>
        <p class="mb-8 text-lg 2xl:text-2xl">
          A welcoming, comforting and inspiring home will improve your life more
          than anything you can do for yourself.
          <br />
          <br />
          Build a home for your family to grow, flourish, love and learn.
        </p>
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-5">
        <img src="/images/portfolio/home/home-4.webp" alt="Hero Image" />
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-6">
        <img src="/images/portfolio/home/home-5.webp" alt="Hero Image" />
      </div>
    </div>
  </main>
</template>

<style scoped>
.content-item img {
  height: 100%;
  object-fit: cover;
  width: 100%;
}
</style>
