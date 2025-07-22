<script setup lang="ts">
import Logo from './components/RoyalLogo.vue'

const activePosterIndex = ref(2)

const posters = [
  {
    label: 'Boney James',
    date: '6.26.2025',
    time: 'Thursday 7:30 PM',
    image: '/boney_james-alpha.png',
    //flyer: '/boney_james.jpg',
    color: 'from-emerald-950/90 hover:to-emerald-900/5',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/boney-james-royal-summer-jazz-series-139371',
  },
  {
    label: 'Najee & Regina Belle',
    date: '7.10.2025',
    time: 'Thursday 7:30 PM',
    image: '/najee__regina_belle-alpha.png',
    //flyer: '/najee__regina_belle.jpg',
    color: 'from-cyan-950/90 hover:to-cyan-900/5',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/najee-and-regina-belle-royal-summer-jazz-series-142329',
  },
  {
    label: 'Dave Koz & Friends',
    date: '8.7.2025',
    time: 'Thursday 7:30 PM',
    image: '/dave_koz-alpha.png',
    flyer: '/dave_koz.png',
    color: 'from-indigo-950/90 hover:to-indigo-900/5',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/dave-koz-and-friends-summer-horns-2025-the-ultimate-summer-part-royal-summer-jazz-series-142333',
  },
]

const sponsors = [
  {
    image: '/sponsors/aloft.png',
    label: 'Aloft Charlotte Ballantyne',
    type: 'supporter',
    css: 'invert-100',
  },
  {
    image: '/sponsors/middle_c_jazz_logo_square_full-07.png',
    label: 'Middle C Jazz',
    type: 'supporter',
    css: '',
  },
  {
    image: '/sponsors/On Stage Concerts Logo.jpg',
    label: 'On Stage Concerts',
    type: 'supporter',
    css: 'invert-100',
  },
    {
    image: '/sponsors/trucore orange labs logo.png',
    label: 'Tru Core Laboratories',
    type: 'sponsor',
    css: '',
  },
  {
    image: '/sponsors/new_york_life logo.png',
    label: 'New York Life',
    type: 'supporter',
    css: '',
  },
]

const activePoster = computed(() => {
  return posters[activePosterIndex.value]
})
</script>

<template>
  <div class="relative clear-both">
    <div class="h-screen relative">
      <div
        class="absolute inset-0 bg-[url(/1.jpg)] bg-cover mix-blend-screen mask-b-from-30% mask-b-to-90% animate-pulse [animation-duration:10s] -z-10"
      ></div>
      <div class="hidden absolute inset-0 sm:grid grid-cols-3 h-screen -z-20">
        <template v-for="item in posters" :key="item.image">
          <div :class="['h-full flex bg-gradient-to-b to-black transition-all', item.color]"></div>
        </template>
      </div>

      <div class="absolute inset-0 h-screen -z-20 sm:hidden">
        <div :class="['h-full flex bg-gradient-to-b to-black', activePoster.color]"></div>
      </div>

      <div class="grid grid-rows-[auto_1fr_5rem_2px] h-screen">
        <div class="flex items-center justify-center w-full">
          <Logo class="h-20 sm:h-[200px] sm:pt-4 fill-white" />
        </div>
        <div>
          <div class="hidden sm:grid grid-cols-3 overflow-clip flex-1 h-full">
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
        <div class="grid grid-cols-3 items-center overflow-clip text-white justify-center">
          <template v-for="(item, index) in posters" :key="item.image">
            <button
              :class="[
                item.color,
                'bg-gradient-to-b to-black sm:text-base text-sm px-2 flex items-center justify-center h-full',
              ]"
              @click="activePosterIndex = index"
            >
              {{ item.label }}
              <span class="hidden sm:block pl-4">{{ item.date }}</span>
            </button>
          </template>
        </div>
        <div class="">
          <div
            :class="[
              'bg-white/50 h-[2px] w-1/3 transition duration-300 ease-in-out',
              activePosterIndex === 1
                ? 'translate-x-full'
                : activePosterIndex === 2
                  ? 'translate-x-[200%]'
                  : activePosterIndex === 3
                    ? 'translate-x-[300%]'
                    : '',
            ]"
          ></div>
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

  <div class="bg-black/10 clear-both mt-40 border  ">
    <section class="max-w-screen-xl mx-auto bg-black/80 px-4 sm:px-10">
      <div class="md:grid grid-cols-1 items-center gap-4 sm:gap-10 py-10">
        <p class="text-center text-[#c39243] text-2xl">Join us for the last show of the series!</p>
        <template v-for="{ flyer: image, label: alt, ticket } in posters.filter(x => x.flyer)" :key="image">
          <div class="overflow-clip  mx-auto">
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
      <a
        class="group block text-white relative overflow-clip mb-10"
        target="_blank"
        href="https://www.marriott.com/event-reservations/reservation-link.mi?id=1749490723959&key=CORP&app=resvlink"
      >
        <img
          src="/aloft-charlotte-ballantyne.jpg"
          alt="Aloft Charlotte Ballantyne"
          class="group-hover:scale-110 w-full mb-4 transition"
        />
        <div class="absolute bottom-0 inset-x-0 p-2 bg-gradient-to-b to-55% to-black/70 pt-10">
          Book your corporate rate for Royal Summer Jazz Series<br />
          at Aloft Charlotte Ballantyne
        </div>
      </a>
      <div class="flex flex-col gap-10 *:border *:border-purple-950">
        <article>
          <h3 class="font-title text-white text-9xl text-center">Sponsors</h3>

          <div class="grid grid-cols-1 gap-4 items-center justify-center">
            <template
              v-for="item in sponsors.filter((x) => x.type === 'sponsor')"
              :key="item.label"
            >
              <img
                :src="item.image"
                :alt="item.label"
                :class="['max-w-4xl w-full mx-auto', item.css]"
              />
            </template>
          </div>
        </article>
        <article>
          <h3 class="font-title text-white text-9xl text-center">Partners</h3>

          <div class="flex items-center gap-10 mt-10 flex-wrap justify-center">
            <template
              v-for="item in sponsors.filter((x) => x.type !== 'sponsor')"
              :key="item.label"
            >
              <div>
                <img :src="item.image" :alt="item.label" :class="['max-w-96', item.css]" />
              </div>
            </template>
          </div>
        </article>
        <article>
          <h3 class="font-title text-white text-9xl text-center">Location</h3>
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
        </article>
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
