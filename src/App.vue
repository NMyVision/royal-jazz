<script setup lang="ts">
import Logo from './components/RoyalLogo.vue'
const events = [
  {
    image: '/boney_james.jpg',
    alt: 'Boney James',
    date: '6.26.25',
    time: 'Thursday 7:30 PM',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/boney-james-royal-summer-jazz-series-139371',
  },
  {
    image: '/najee__regina_belle.jpg',
    alt: 'Najee & Regina Belle',
    date: '7.10.25',
    time: 'Thursday 7:30 PM',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/najee-and-regina-belle-royal-summer-jazz-series-142329',
  },
  {
    image: '/will_downing.jpg',
    alt: 'Will Downing',
    date: '7.24.25',
    time: 'Thursday 7:30 PM',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/will-downing-royal-summer-jazz-series-142330',
  },
  {
    image: '/koz.jpg',
    alt: 'Dave KOZ & Friends',
    date: '8.7.25',
    time: 'Thursday 7:30 PM',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/dave-koz-and-friends-summer-horns-2025-the-ultimate-summer-part-royal-summer-jazz-series-142333',
  },
]

const activePosterIndex = ref(0)

const posters = [
  {
    label: 'Boney James',
    date: '6.26.2025',
    image: '/boney_james-alpha.png',
    color: 'from-emerald-950/90',
  },
  {
    label: 'Najee & Regina Belle',
    date: '7.10.2025',
    image: '/najee__regina_belle-alpha.png',
    color: 'from-cyan-950/90',
  },
  {
    label: 'Will Downing',
    date: '7.24.2025',
    image: '/will_downing-alpha.png',
    color: 'from-rose-950/90',
  },
  {
    label: 'David Koz & Friends',
    date: '8.7.2025',
    image: '/david_koz-alpha.png',
    color: 'from-indigo-950/90',
  },
]

const activePoster = computed(() => {
  return posters[activePosterIndex.value]
})
</script>

<template>
  <div class="relative">
    <div class="h-screen relative">
      <div
        class="absolute inset-0 bg-[url(/1.jpg)] bg-cover mix-blend-screen mask-b-from-30% mask-b-to-90% animate-pulse [animation-duration:10s] -z-10"
      ></div>
      <div class="hidden absolute inset-0 sm:grid grid-cols-4 h-screen -z-20">
        <template v-for="item in posters" :key="item.image">
          <div :class="['h-full flex bg-gradient-to-b to-black transition-all', item.color]"></div>
        </template>
      </div>

      <div class="absolute inset-0 h-screen -z-20 sm:hidden">
        <div :class="['h-full flex bg-gradient-to-b to-black', activePoster.color]"></div>
      </div>

      <div class="grid grid-rows-[6rem_1fr_5rem_2px] h-screen">
        <div class="flex items-center justify-center w-full">
          <Logo class="h-20 sm:h-[200px] fill-white" />
        </div>
        <div>
          <div class="hidden sm:grid grid-cols-4 overflow-clip flex-1 h-full">
            <template v-for="item in posters" :key="item.image">
              <img
                :src="item.image"
                class="shrink-0 flex-none object-cover self-end transition duration-200 ease-in-out hover:scale-120"
              />
            </template>
          </div>
          <div
            class="block sm:hidden bg-cover bg-center h-full"
            :style="{ backgroundImage: `url(${activePoster.image})` }"
          >
            <img :src="activePoster.image" class="opacity-0" />
          </div>
        </div>
        <div class="grid grid-cols-4 items-center overflow-clip text-white justify-center">
          <template v-for="(item, index) in posters" :key="item.image">
            <button
              :class="[item.color, 'bg-gradient-to-b to-black sm:text-base text-sm px-2 flex items-center justify-center h-full']"
              @click="activePosterIndex = index"
            >
              {{ item.label }}
              <span class="hidden sm:block pl-4">{{ item.date }}</span>
            </button>
          </template>
        </div>
        <div class="">
          <div :class="['bg-white/50 h-[2px] w-1/4 transition duration-300 ease-in-out', activePosterIndex === 1 ? 'translate-x-full' : activePosterIndex === 2 ?  'translate-x-[200%]' : activePosterIndex === 3 ?  'translate-x-[300%]' :'']"></div>
        </div>
      </div>

      <!-- <div class="sm:hidden grid grid-rows-[6rem_1fr_5rem] h-screen min-w-full">
        <div></div>
        <div class="bg-cover bg-center" :style="{ backgroundImage: `url(${activePoster.image})` }">
          <img :src="activePoster.image" class="opacity-0" />
        </div>
        <div class="text-white grid grid-cols-4">
          <template v-for="(item, index) in posters" :key="item.image">
            <button
              :class="[item.color, 'to-black sm:text-base text-sm px-2 flex h-20']"
              @click="activePosterIndex = index"
            >
              {{ item.label }}
              <span class="hidden sm:block">{{ item.date }}</span>
            </button>
          </template>
        </div>
      </div> -->
    </div>
  </div>

  <div class="bg-black/10">
    <section class="max-w-screen-xl mx-auto bg-black/80 px-4 sm:px-10">
      <div class="md:grid grid-cols-2 items-center gap-4 sm:gap-10 py-10">
        <template v-for="{ image, alt, ticket } in events" :key="image">
          <div class="overflow-clip">
            <a class="block" :href="ticket" target="_blank" rel="noopener">
              <img :src="image" :alt="alt" height="auto" width="675px" class="hover:scale-110" />
            </a>
          </div>
        </template>
      </div>
      <div class="p-10 text-center">
        <a
          class="inline-block border-white/50 border-2 bg-[#b46a20] text-[#f1ed74]/90 py-4 px-8 uppercase font-medium rounded-full"
          href="https://www.ampballantyne.com"
          >Buy Tickets</a
        >
      </div>

      <div class="sm:p-10 relative w-full">
        <div class="overflow-hidden !bg-transparent w-full h-400px">
          <iframe
            class="gmap_iframe"
            width="100%"
            frameborder="0"
            scrolling="no"
            marginheight="0"
            marginwidth="0"
            src="https://maps.google.com/maps?width=800&amp;height=400&amp;hl=en&amp;q=11115 upper ave&amp;t=&amp;z=14&amp;ie=UTF8&amp;iwloc=B&amp;output=embed"
          ></iframe
          ><a href="https://embed-googlemap.com">embed google maps in website</a>
        </div>
      </div>
    </section>
  </div>
</template>

<style>
.mapouter {
  position: relative;
  text-align: right;
  width: 100%;
  height: 400px;
}
.gmap_canvas {
  overflow: hidden;
  background: none !important;
  width: 100%;
  height: 400px;
}
.gmap_iframe {
  height: 400px !important;
}
</style>
