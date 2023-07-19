<script setup>
import { onMounted } from "vue";
const emit = defineEmits(["homeLoaded"]);
onMounted(() => {
  emit("homeLoaded");
});
</script>

<template>
  <article
    class="xl:max-w-screen-xl 2xl:max-w-screen-2xl 3xl:max-w-screen-3xl | mx-auto p-8 lg:p-8 2xl:p-16"
  >
    <div
      class="grid grid-cols-2 xl:grid-cols-3 xl:grid-rows-2 gap-2 xl:gap-8 grid-flow-row-dense"
    >
      <div class="content-item | col-span-1 row-span-1 xl:order-1">
        <img
          src="/images/portfolio/home/home-1.webp"
          alt="Hero Image"
          data-aos="fade-down"
          data-aos-delay="100"
        />
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-2">
        <img
          src="/images/portfolio/home/home-2.webp"
          alt="Hero Image"
          data-aos="fade-down"
          data-aos-delay="200"
        />
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-3">
        <img
          src="/images/portfolio/home/home-3.webp"
          alt="Hero Image"
          data-aos="fade-down"
          data-aos-delay="300"
        />
      </div>
      <div
        class="content-item | col-span-2 xl:col-span-1 row-span-1 | p-8 | flex flex-col align-center justify-center | order-first xl:order-4"
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
        <img
          src="/images/portfolio/home/home-4.webp"
          alt="Hero Image"
          data-aos="fade-down"
          data-aos-delay="400"
        />
      </div>
      <div class="content-item | col-span-1 row-span-1 xl:order-6">
        <img
          src="/images/portfolio/home/home-5.webp"
          alt="Hero Image"
          data-aos="fade-down"
          data-aos-delay="500"
        />
      </div>
    </div>
  </article>
</template>

<style scoped>
.content-item img {
  height: 100%;
  object-fit: cover;
  width: auto;
  transition: 0.75s all linear;
}

@media (max-aspect-ratio: 3/4) {
  .content-item img {
    aspect-ratio: 3/4;
  }
}
@media (min-aspect-ratio: 3/4) and (max-aspect-ratio: 1/1) {
  .content-item img {
    aspect-ratio: 1;
  }
}
@media (min-aspect-ratio: 1) and (max-aspect-ratio: 1.33) {
  .content-item img {
    aspect-ratio: 0.95;
  }
}
@media (min-aspect-ratio: 1.33) {
  .content-item img {
    aspect-ratio: 4/3;
  }
}
@media (min-aspect-ratio: 1.75) {
  .content-item img {
    aspect-ratio: 1.25;
  }
}
@media (min-aspect-ratio: 1.75) and (max-aspect-ratio: 2.1) {
  .content-item img {
    aspect-ratio: 1.65;
  }
}
@media (min-aspect-ratio: 2.1) and (max-aspect-ratio: 3) {
  .content-item img {
    aspect-ratio: 1.75;
  }
}
@media (min-height: 1280px) and (min-aspect-ratio: 1) {
  .content-item img {
    aspect-ratio: 1.25;
  }
}
</style>
