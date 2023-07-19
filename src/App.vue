<script setup>
import { onMounted, watch, defineAsyncComponent } from "vue";
import { storeToRefs } from "pinia";

// router
import { useRoute, useRouter } from "vue-router";

// nav store
import { useNavStore } from "@/stores/navStore";

// components
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";

// views
import HomeView from "@/views/HomeView.vue";

// swiper
import { register } from "swiper/element/bundle";
register();
const spaceBetween = 10;

// aos
import AOS from "aos";
import "aos/dist/aos.css"; // You can also use <link> for styles
// ..
AOS.init();

// register routes from store
const router = useRouter();

const { navItems } = useNavStore();

console.log(navItems);
navItems.forEach((item) => {
  router.addRoute(item);
});

const onProgress = (e) => {
  // const [swiper, progress] = e.detail;
  // console.log(progress, swiper.activeIndex);
};

const onSlideChange = (e) => {
  console.log("slide changed", e.target.swiper.activeIndex, router);
  const slide = document.querySelector(
    'swiper-slide[data-slideid="' + e.target.swiper.activeIndex + '"]'
  );
  const slidePath = slide.dataset.path;
  router.push(slidePath);
};

const mainSlideChange = (direction) => {
  const swiper = document.getElementById("main-swiper").swiper;
  if (direction === "next") {
    swiper.slideNext();
  } else {
    swiper.slidePrev();
  }
};

onMounted(() => {
  let route = useRoute();
  watch(
    () => route.path,
    (newVal, oldVal) => {
      const swiper = document.getElementById("main-swiper").swiper;
      const slide = document.querySelector(
        'swiper-slide[data-path="' + newVal + '"]'
      );
      console.log(slide, newVal);
      const slideId = slide.dataset.slideid;
      console.log("route changed", "sliding to", slideId, newVal);
      swiper.slideTo(slideId);
    }
  );
});

//watch router path
</script>

<template>
  <div class="app-wrapper | w-full | grid grid-cols-1 grid-rows-3">
    <Header />
    <main class="main">
      <swiper-container
        id="main-swiper"
        :slides-per-view="1"
        :space-between="spaceBetween"
        :centered-slides="true"
        :speed="600"
        :mousewheel="{
          sensitivity: 0.00015,
          thresholdTime: 350,
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
        class="h-full"
      >
        <swiper-slide
          :id="'main-swiper--' + route.name"
          :data-path="route.path"
          :data-slideid="index"
          v-for="(route, index) in navItems"
          :key="index"
          class="flex items-center"
        >
          <component :is="defineAsyncComponent(route.component)"></component>
        </swiper-slide>
      </swiper-container>
    </main>

    <Footer
      @main-swiper--prev="mainSlideChange('prev')"
      @main-swiper--next="mainSlideChange('next')"
    />
  </div>
</template>

<style scoped>
.app-wrapper {
  width: 100vw;
  height: 100vh;
  grid-template-rows: 70px auto 70px;
}
</style>
