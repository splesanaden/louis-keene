<script setup>
import { RouterLink, RouterView } from "vue-router";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";

import { register } from "swiper/element/bundle";
import { onMounted } from "vue";
import HomeView from "./views/HomeView.vue";

register();

const spaceBetween = 10;
const onProgress = (e) => {
  const [swiper, progress] = e.detail;
  console.log(progress);
};

const onSlideChange = (e) => {
  console.log("slide changed");
};

const mainSlideChange = (direction) => {
  const swiper = document.getElementById("main-swiper").swiper;
  if (direction === "next") {
    swiper.slideNext();
  } else {
    swiper.slidePrev();
  }
};

onMounted(() => {});
</script>

<template>
  <Header />

  <!-- <RouterView /> -->

  <swiper-container
    id="main-swiper"
    :slides-per-view="1"
    :space-between="spaceBetween"
    :centered-slides="true"
    :mousewheel="{
      sensitivity: 0.00015,
    }"
    :navigation="{
      nextEl: '.footer-btn--next',
      prevEl: '.footer-btn--prev',
    }"
    :pagination="false"
    :breakpoints="{
      768: {
        slidesPerView: 1,
      },
    }"
    :observer="true"
    :observeParents="true"
    :parallax="true"
    @progress="onProgress"
    @slidechange="onSlideChange"
  >
    <swiper-slide id="main-swiper--home" data-path="home">
      <HomeView />
    </swiper-slide>
    <swiper-slide id="main-swiper--portfolio" data-path="portfolio">
      Portfolio
    </swiper-slide>
    <swiper-slide id="main-swiper--about" data-path="about"
      >Slide 3</swiper-slide
    >
  </swiper-container>

  <Footer
    @main-swiper--prev="mainSlideChange('prev')"
    @main-swiper--next="mainSlideChange('next')"
  />
</template>

<style scoped></style>
