<template>
  <!-- lg:py-4 -->
  <div class=" dir-ltr">
    <div
      ref="headerRef"
      class="sm:flex hidden bg-white dark:bg-gray-900 w-full sm:h-[70px] items-center transition-all duration-500 transform overflow-hidden header-wrapper fixed top-0"
    >
      <div class="container max-h-full h-full" style="font-size: 12px;">
        <div class="flex items-center justify-between h-full">
          <div class="h-full">
            <NuxtLink :to="$tm('brand.link')">
              <h3
                class="font-extrabold font-[inter-extrabold] capitalize lg:text-xl text-black dark:text-white h-full"
                 style="margin-left: -30px;"
              >
                <!-- {{ $tm("brand.value") }} -->
                <img src="/images/infFITS_Logo.png" alt="logo" class="max-h-full ">
              </h3>
            </NuxtLink>
          </div>

          <ul class="flex items-center ">
            <li class="lg:mx-4 mx-2">
              <!-- button前的東西 -->
              <ul class="flex ltr:dir-ltr rtl:dir-rtl items-center " >
                <li
                  v-for="(item, index) in $tm(
                    'components.layouts.header.items'
                  )"
                  :key="index"
                >
                  <NuxtLink
                    :to="item.link"
                    :class="[
                      'lg:mx-4 mx-2 hover:text-baseYellow-500 duration-500 ',
                      currentAcitveRoute &&
                      currentAcitveRoute.link === item.link
                        ? 'text-baseYellow-500'
                        : '',
                    ]"
                    >{{ item.text }}</NuxtLink
                  >
                </li>
              </ul>
            </li>
            <!-- button -->
            <li
              class="lg:w-[142px] h-10 block rounded-full hover:bg-baseYellow-700 duration-500 text-white px-4"
              style="background-color: black;"
            >
              <NuxtLink
                class="w-full h-full flex justify-center items-center  font-bold"
                :to="$tm('components.layouts.header.login.link')"
                >{{ $tm("components.layouts.header.login.text") }}</NuxtLink
              >
            </li>
            <!-- <li class="lg:mx-4 mx-2">
              <div class="w-[120px] h-10">
                <ClientOnly>
                  <ElementDropdownMenu
                    :selected="getCurrentLanguageFromI18n"
                    :items="$tm('other.languages') as Language[]"
                    @on-change-selected-item="onChangeSelectedLanguage"
                  />
                </ClientOnly>
              </div>
            </li> -->
            <!-- <li v-if="useAuthState().value" class="lg:mx-1 mx-0.5">
              <div class="flex items-center">
                <div
                  class="mx-auto w-10 h-10 border-2 border-gray-200 dark:border-gray-700 rounded-full flex items-center justify-center"
                  :title="useAuthState().value?.email"
                >
                  <div class="w-5 h-5">
                    <ElementIcon
                      :icon="{ prefix: 'fa-regular', value: 'fa-user' }"
                      variant="default"
                    />
                  </div>
                </div>
              </div>
            </li> -->
          </ul>
        </div>
      </div>
    </div>
    <!-- 手機 -->
    <div class="sm:hidden block bg-black text-white">
      <div class="w-full flex items-center">
        <div class="p-4 w-full">
          <div class="w-full flex items-center justify-between">
            <div>
              <NuxtLink :to="$tm('brand.link')">
                <h3
                  class="font-extrabold text-white font-[inter-extrabold] capitalize text-base"
                >
                  {{ $tm("brand.value") }}
                </h3>
              </NuxtLink>
            </div>
            <div>
              <div class="w-5 h-5 cursor-pointer" @click="onToggleHeaderItems">
                <ElementIcon
                  :icon="{ prefix: 'fa-solid', value: 'fa-bars' }"
                  variant="white"
                />
              </div>
            </div>
          </div>
          <ul
            :style="{ height: dynamicResponsiveHeaderItemsHeight + 'px' }"
            :class="[
              isResponsiveHeaderOpen
                ? 'opacity-1 overflow-y-visible mt-4'
                : 'opacity-0 overflow-y-hidden mt-0',
            ]"
            ref="responsiveHeaderItemsRef"
            class="transition-all duration-500 ltr:dir-ltr rtl:dir-rtl"
          >
            <li
              v-for="(item, index) in $tm('components.layouts.header.items')"
              :key="index"
              class="mb-4"
            >
              <NuxtLink
                :to="item.link"
                :class="[
                  ' hover:text-baseYellow-500 duration-500 ',
                  currentAcitveRoute && currentAcitveRoute.link === item.link
                    ? 'text-baseYellow-500'
                    : '',
                ]"
                >{{ item.text }}</NuxtLink
              >
            </li>
            <li class="mb-4">
              <div class="flex">
                <div class="w-1/2 h-10">
                  <div class="w-full h-full p-1">
                    <ClientOnly>
                      <ElementDropdownMenu
                        :selected="getCurrentLanguageFromI18n"
                        :items="$tm('other.languages') as Language[]"
                        variant="black"
                        position="top"
                        @on-change-selected-item="
                          onChangeSelectedLanguage($event as Language)
                        "
                      />
                    </ClientOnly>
                  </div>
                </div>
                <div class="w-1/2 h-10">
                  <div class="w-full h-full p-1">
                    <ClientOnly>
                      <ElementDropdownMenu
                        :selected="getCurrentTheme"
                        :items="$tm('other.themes') as Theme[]"
                        variant="black"
                        position="top"
                        @on-change-selected-item="
                          onChangeTheme($event.value as ThemeVariants)
                        "
                      />
                    </ClientOnly>
                  </div>
                </div>
              </div>
            </li>
            <li
              v-if="!useAuthState().value"
              class="w-full h-10 block rounded-md bg-baseYellow-500 hover:bg-baseYellow-700 duration-500 text-white"
            >
              <NuxtLink
                class="w-full h-full flex justify-center items-center font-bold"
                :to="$tm('components.layouts.header.login.link')"
                >{{ $tm("components.layouts.header.login.text") }}</NuxtLink
              >
            </li>

            <li v-if="useAuthState().value">
              <div
                class="mx-auto w-10 h-10 border border-gray-700 rounded-full flex items-center justify-center"
              >
                <div class="w-5 h-5 cursor-pointer">
                  <ElementIcon
                    :icon="{ prefix: 'fa-regular', value: 'fa-user' }"
                    variant="white"
                  />
                </div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useToast } from "vue-toastification";
import type {
  Link,
  Language,
  AvailableLanguageCodes,
  Theme,
  ThemeVariants,
} from "~/utilities/types";
// interfaces & types & enums

// props
// emits

// variables
const route = useRoute();
const { $i18n } = useNuxtApp();
const { onChangeLanguage, getCurrentLanguageFromI18n } = useLanguage();
const { onChangeTheme, getCurrentTheme } = useTheme();

const currentAcitveRoute = ref<Link | null>(null);
const isResponsiveHeaderOpen = ref<boolean>(false);
const headerRef = ref<HTMLDivElement | null>(null);
const dynamicResponsiveHeaderItemsHeight = ref<number>(0);
const responsiveHeaderItemsRef = ref<HTMLDivElement | null>(null);

// computed properties

// watches
watch(
  () => route.path,
  () => {
    // Get current route and set its element active
    const i18nRouteItems: Link[] = $i18n.tm("components.layouts.header.items");
    const foundedI18nRoute = i18nRouteItems.find((item: Link) => {
      return item.link === route.path;
    });
    if (foundedI18nRoute) {
      currentAcitveRoute.value = foundedI18nRoute;
    } else {
      currentAcitveRoute.value = null;
    }
  },
  { immediate: true }
);
// methods
const onToggleHeaderItems = () => {
  isResponsiveHeaderOpen.value = !isResponsiveHeaderOpen.value;

  if (responsiveHeaderItemsRef.value) {
    isResponsiveHeaderOpen.value
      ? (dynamicResponsiveHeaderItemsHeight.value =
          responsiveHeaderItemsRef.value.scrollHeight)
      : (dynamicResponsiveHeaderItemsHeight.value = 0);
  }
};
const onVerticalScrollbar = (element: any, amount: number) => {
  const scrollPosition = window.scrollY || window.pageYOffset;

  if (scrollPosition > amount) {
    element.classList.add(
      ...[
        "fixed",
        "z-10",
        "top-0",
        "bg-white",
        "dark:bg-black",
        "drop-shadow-md",
      ]
    );
  } else {
    element.classList.remove(
      ...[
        // "fixed",
        "z-10",
        // "top-0",
        "bg-white",
        "dark:bg-black",
        "drop-shadow-md",
      ]
    );
  }
};
const onChangeSelectedLanguage = (language: Language) => {
  const toast = useToast();

  onChangeLanguage(language.value as AvailableLanguageCodes);
  onChangeFontFamily(language.value as AvailableLanguageCodes);
  
  toast.clear();
};

// hooks
onMounted(() => {
  window.addEventListener("scroll", () => {
    onVerticalScrollbar(headerRef.value, 0);
  });
});
onUnmounted(() => {
  window.removeEventListener("scroll", () => {
    onVerticalScrollbar(headerRef.value, 0);
  });
});

// hooks
</script>
<style scoped lang="css">

.header-wrapper {
  border-bottom: 1.5px solid #1f1e1e; 
}

</style>
