<template>
  <div>
    <!-- lg:pt-8 -->
    <div class="bg-white dark:bg-gray-900  lg:pb-0 py-2 " style="background: linear-gradient(135deg, white 0%, #e0d58c 100%); margin-top:70px;" >
      <div class="container">
        <MainHomeIntroduction />
      </div>
    </div>

    <div class="lg:py-0 py-4 dark:bg-[#fda] my-24">
      <div class="container lg:px-4 px-2">
        <MainHomeOurPartners />
      </div>
    </div>

    <div class="lg:py-20 py-4 ">
      <div class="container lg:px-4 px-2">
        <div
          class="lg:mb-8 mb-4 text-center latest-posts-animate-box animate__animated"
        >
          <h1
            class="lg:text-4xl text-2xl font-extrabold text-black dark:text-white"
          >
            {{ $tm("components.pages.home.dauntForSales.title") }}
          </h1>
        </div>

        <MainHomeDaunt :daunts="($tm('components.pages.home.dauntForSales.values')  as string[] )" />
       

      </div>
    </div>

    

    <div class="lg:py-20 py-4">
      <div class=" ">
        <!-- <MainHomeWhyChooseUs /> -->
         <MainHomeInfFITSBenefits />
      </div>
    </div>

    <div class="lg:py-0 py-4 dark:bg-[#fda]">
      <div class="container lg:px-4 px-2">
        <MainHomeOurPartners />
      </div>
    </div>

    <div class="lg:py-20 py-4">
      <div class="container lg:px-4 px-2">
        <div
          class="lg:mb-8 mb-4 text-center latest-posts-animate-box animate__animated"
        >
          <h1
            class="lg:text-4xl text-2xl font-extrabold text-black dark:text-white"
          >
            {{ $tm("components.pages.home.howItWorks.title") }}
          </h1>
        </div>

        <MainHomeHowItWorks :how="($tm('components.pages.home.howItWorks.findSize')  as Object )" />
        <div class="lg:pt-20 pt-4"></div>
        <MainHomeHowItWorks :how="($tm('components.pages.home.howItWorks.findProduct')  as Object )" />

      </div>
    </div>

    <div class="bg-white dark:bg-gray-900  lg:pb-0 py-2 pt-0" style="background: linear-gradient(135deg, #fdfbfb 0%, #ebedee 100%);">
      <div class="container">
        <MainHomeBookADemo />
      </div>
    </div>


    <div class="bg-baseYellow-700 text-white">
      <div class="lg:py-20 py-4">
        <div class="container lg:px-4 px-2">
          <MainHomeTrustedCustomers />
        </div>
      </div>
    </div>
    <div class="bg-white dark:bg-gray-900 lg:py-20 py-4">
      <div class="container lg:px-4 px-2">
        <MainHomeOurMainServices />
      </div>
    </div>
    

    <div class="bg-white dark:bg-gray-900 lg:py-20 py-4">
      <div class="container lg:px-4 px-2">
        <MainHomeOurBestPricing />
      </div>
    </div>
    
  </div>


  
  <div class="lg:py-20 py-4">
    <div class="container lg:px-4 px-2">
      <div
        class="lg:mb-8 mb-4 text-center latest-posts-animate-box animate__animated"
      >
        <h1
          class="lg:text-4xl text-2xl font-extrabold text-black dark:text-white"
        >
          {{ $tm("components.pages.home.latestContent.title") }}
        </h1>
      </div>
      <ul
        class="flex items-center justify-center lg:-mx-2 -mx-1 lg:mb-16 mb-8"
      >
        <li
          v-for="(tab, index) in ($tm('components.pages.home.latestContent.tabs') as Tab[])"
          :key="index"
          @click="selectedLatestContentTab = tab"
        >
          <div
            class="lg:mx-2 mx-1 lg:w-[160px] lg:h-[52px] w-fit lg:p-0 p-2 border border-baseYellow-500 text-baseYellow-500 hover:bg-baseYellow-700 hover:border-baseYellow-700 hover:text-white duration-500 cursor-pointer rounded-md"
            :class="
              selectedLatestContentTab?.value === tab.value
                ? 'border-baseYellow-700 bg-baseYellow-700 text-white'
                : ''
            "
          >
            <NuxtLink
              :to="`?tab=${tab.value}`"
              class="font-bold lg:text-xl text-sm w-full h-full flex items-center justify-center"
              >{{ tab.text }}</NuxtLink
            >
          </div>
        </li>
      </ul>

      <Transition
        v-if="selectedLatestContentTab?.value === 'podcasts'"
        name="page"
        mode="out-in"
        appear
      >
        <MainHomeLatestPodcasts :podcasts="podcasts as Podcast[]" />
      </Transition>

      <Transition
        v-else-if="selectedLatestContentTab?.value === 'posts'"
        name="page"
        mode="out-in"
        appear
      >
        <MainHomeLatestPosts :posts="posts as Post[]" />
      </Transition>

      <Transition
        v-else-if="selectedLatestContentTab?.value === 'videos'"
        name="page"
        mode="out-in"
        appear
      >
        <MainHomeLatestVideos :videos="videos as Video[]" />
      </Transition>
    </div>
  </div>

</template>

<script setup lang="ts">
import type { Podcast, Post, Video } from "~/utilities/types";

// interfaces & types & enums
interface Tab {
  text: string;
  value: string;
}
// props

// emits

// variables
const { tm, locale } = useI18n();
const route = useRoute();
const latestContentTab: Tab[] = tm("components.pages.home.latestContent.tabs");
const selectedLatestContentTab = ref<Tab | null>(null);
// computed properties

// watches
watch(
  () => route.query,
  () => {
    fetchCurrentTabFromI18n();
  }
);

// methods
const fetchCurrentTabFromI18n = () => {
  const foundedTab = latestContentTab.find(
    (tab: Tab) => tab.value === route.query["tab"]
  );
  if (foundedTab) {
    selectedLatestContentTab.value = foundedTab;
  } else {
    selectedLatestContentTab.value = latestContentTab[0];
  }
};

// hooks
const { data: podcasts } = await useFetch(
  `/api/podcasts?locale=${locale.value}`
);
const { data: videos } = await useFetch(`/api/videos?locale=${locale.value}`);
const { data: posts } = await useFetch(`/api/posts?locale=${locale.value}`);

onMounted(() => {
  fetchCurrentTabFromI18n();
});

useHead({
  title: tm("components.pages.home.meta.title"),
  meta: [
    {
      name: tm("components.pages.home.meta.name"),
      content: tm("components.pages.home.meta.content"),
    },
  ],
});
</script>
<style scoped lang="scss"></style>
