<script setup lang="ts">
import { onMounted, onUnmounted, useTemplateRef } from 'vue'
import Logo from './components/RoyalLogo.vue'
import BoneyJames from './components/BoneyJames.vue'
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

const scrollContainer = useTemplateRef<HTMLElement | null>('scrollContainer')

const onScroll = () => {
  if (!scrollContainer.value) return
  // Adjust the multiplier for desired scroll speed
  scrollContainer.value.scrollLeft = window.scrollY
}

onMounted(() => {
  window.addEventListener('scroll', onScroll)
})
onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
//  \assets\img\najee__regina_belle.jpg
//  /assets/img/najee__regina_belle.jpg
</script>

<template>
  <Logo class="fill-white z-20 aspect-video origin-center self-start w-96 scale-75" />

  <div ref="scrollContainer" class="min-h-screen flex-nowrap flex items-center w-screen fixed">
    <div
      class="fixed left-0 inset-y-0 -z-10 bg-[#d0c1e8] bg-[url('/poster-a-back.jpg')] bg-fixed min-h-screen w-screen"
    ></div>
    <div class="relative"></div>
    <img
      src="/boney_james_poster-trans-nologo.png"
      class="object-cover min-h-screen w-fit"
      alt=""
    />
    <img
      src="/najee_regina_belle-wide_poster-trans-nologo.png"
      class="object-cover min-h-screen w-fit"
      alt=""
    />
    <img
      src="/will_downing_poster-trans-nologo.png"
      alt=""
      class="object-cover min-h-screen sm:min-h-0"
    />
    <img src="/david_koz_poster-trans-nologo.png" alt="" class="object-cover min-h-screen" />
  </div>
  <!-- ...rest of your template... -->

  <!-- <div class="grid stacked bg-[#d0c1e8] min-h-screen">
    <Logo class="fill-white z-20 aspect-video scale-50 origin-center self-start" />
    <img src="/poster-a-back.jpg" />
    <div class="scale-80">
      <BoneyJames />
    </div>
    <img src="/poster-a-foreground.png" alt="" class="scale-70 origin-bottom self-end">
  </div> -->

  <div class="bg-black/50" v-if="false">
    <section class="max-w-screen-xl mx-auto bg-black/80 px-4 sm:px-10">
      <div class="grid items-center justify-center p-10">
        <Logo class="h-[600px] fill-white" />
      </div>
      <div class="relative grid stacked">
        <div class="absolute z-20">
          <img src="/poster-a-foreground.png" alt="" />
        </div>
        <div class="absolute" v-if="false">
          <img src="/series_promo.jpg" alt="alt" />
        </div>
      </div>
      <div class="md:grid grid-cols-2 items-center gap-x-4 md:gap-10 py-10">
        <template v-for="{ image, alt, ticket, date, time } in events" :key="image">
          <a
            class="group block relative overflow-clip mb-10 sm:mb-0"
            :href="ticket"
            target="_blank"
            :rel="noreferrer"
          >
            <div class="relative overflow-clip">
              <img :src="image" class="invisible" :alt="alt" height="auto" width="675px" />
              <div
                class="absolute inset-0 bg-blue-100 hover:scale-110 bg-cover"
                :style="{ backgroundImage: `url(${image})` }"
              ></div>
            </div>
            <div class="bg-black bottom-0 text-white">
              <p>{{ date }} - {{ time }}</p>
              Buy Tickets
            </div>
          </a>
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

  <div :style="{height: scrollContainer.width + 'px'}" class="h-[1240px]" ></div>
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

.stacked > * {
  grid-row-start: 1;
  grid-column-start: 1;
}
</style>
