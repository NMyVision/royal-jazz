<script setup lang="ts">
import Logo from './components/RoyalLogo.vue'
const events = [
  {
    image: '/src/assets/img/boney_james.jpg',
    alt: 'Boney James',
    date: 'June 26, 2025',
    ticket:
      'https://www.tixr.com/groups/ampballantyne/events/boney-james-royal-summer-jazz-series-139371',
  },
  {
    image: '/src/assets/img/najee__regina_belle.jpg',
    alt: 'Najee & Regina Belle',
    date: 'July 10, 2025',
  },
  {
    image: '/src/assets/img/will_downing.jpg',
    alt: 'Will Downing',
    date: 'July 24, 2025',
  },
]
//  \assets\img\najee__regina_belle.jpg
//  /assets/img/najee__regina_belle.jpg
</script>

<template>
  <div class="bg-black/50">
    <section class="max-w-screen-xl mx-auto bg-black/80 px-4 sm:px-10">
      <div class="grid items-center justify-center p-10">
        <Logo class="h-[600px] fill-white" />
      </div>
      <div class="md:flex items-center gap-4 py-10">
        <template v-for="{ image, alt } in events" :key="image">
          <a class="block" href="https://www.ampballantyne.com">
            <img :src="image" :alt="alt" height="auto" width="675px" />
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
