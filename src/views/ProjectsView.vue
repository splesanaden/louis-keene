<script setup>
import { onMounted, ref, computed } from "vue";
const portfolioApiEndpoint =
  "https://louis.goteam2.dev/wp-json/wp/v2/portfolio?order=asc&per_page=100";

const portfolioItems = ref({});
const portfolioError = ref(null);
let activePortfolioItem = ref(0);

let getActivePortfolioItem = computed(() => {
  if (!portfolioItems.value) return {};
  return portfolioItems.value[activePortfolioItem.value];
});
let setActivePortfolioItem = (index) => {
  activePortfolioItem.value = index;
};
onMounted(async () => {
  try {
    const response = await fetch(portfolioApiEndpoint);
    portfolioItems.value = await response.json();
    activePortfolioItem.value = 0;
  } catch (err) {
    portfolioError.value = err;
  }
});
</script>

<template>
  <article
    class="xl:max-w-screen-xl 2xl:max-w-screen-2xl 3xl:max-w-screen-3xl | mx-auto p-8 lg:p-8 2xl:p-16"
  >
    <div
      class="portfolio | w-full | grid justify-stretch"
      v-if="!portfolioError"
    >
      <nav class="portoflio-nav | grid grid-flow-col">
        <div
          class="portfolio-nav--link"
          :class="index == activePortfolioItem ? 'portfolio-active' : ''"
          v-for="(item, index) in portfolioItems"
          role="button"
          @click="setActivePortfolioItem(index)"
        >
          {{ item.title.rendered }}
        </div>
      </nav>
      <div class="portfolio-display | mt-4" v-if="getActivePortfolioItem">
        <div
          class="portfolio-grid | grid grid-cols-8 grid-rows-2 grid-flow-col gap-6 | h-[420px] | items-stretch"
        >
          <div class="portfolio-grid--col | col-span-3 row-span-2">
            <img
              :src="getActivePortfolioItem.meta.gallery[0].url"
              :alt="getActivePortfolioItem.title.rendered + ' image 1'"
              class="portfolio-grid--img | w-auto h-full"
            />
          </div>
          <div class="portfolio-grid--col | col-span-1 row-span-2">
            <img
              :src="getActivePortfolioItem.meta.gallery[1].url"
              :alt="getActivePortfolioItem.title.rendered + ' image 2'"
              class="portfolio-grid--img | w-auto h-full"
            />
          </div>
          <div
            class="portfolio-grid--col description-col | col-span-2 row-span-2 | flex flex-col | p-8"
          >
            <h2 class="text-3xl font-bold">
              {{ getActivePortfolioItem.title.rendered }}
            </h2>
            <div
              class="text-xl | mt-4"
              v-html="getActivePortfolioItem.excerpt.rendered"
            ></div>
            <router-link
              :to="getActivePortfolioItem.link"
              class="border border-zinc-950 bg-white hover:bg-zinc-950 hover:text-white | px-8 py-4 mt-auto | text-2xl font-bold | flex self-start"
            >
              View Project
            </router-link>
          </div>
          <div class="portfolio-grid--col | col-span-3 row-span-1">
            <img
              :src="getActivePortfolioItem.meta.gallery[2].url"
              :alt="getActivePortfolioItem.title.rendered + ' image 3'"
              class="portfolio-grid--img | w-auto h-full"
            />
          </div>
          <div class="portfolio-grid--col | col-span-3 row-span-1">
            <img
              :src="getActivePortfolioItem.meta.gallery[3].url"
              :alt="getActivePortfolioItem.title.rendered + ' image 4'"
              class="portfolio-grid--img | w-auto h-full"
            />
          </div>
        </div>
      </div>
    </div>
  </article>
</template>

<style scoped lang="scss">
.portfolio-nav--link {
  font-size: 1.5rem;
  font-weight: 700;
  color: theme("colors.zinc.700");
  border: 1px solid transparent;
  border-color: transparent theme("colors.zinc.950") transparent;
  background-color: transparent;
  text-align: center;
  min-width: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 16px 20px;
  transition: all 0.2s linear;

  &:last-child {
    border-right: 1px solid transparent;
  }

  &:hover {
    color: theme("colors.zinc.50");
    background-color: theme("colors.zinc.950");
  }
  &:focus,
  &.portfolio-active {
    color: white;
    background-color: theme("colors.zinc.950");
  }
  &:active {
    color: white;
    background-color: theme("colors.zinc.700");
  }
}
.portfolio-grid--img {
  object-fit: cover;
  object-position: top;
}
.description-col p {
  margin-bottom: 1.5rem;
}
</style>
