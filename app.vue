<script setup>


const events = [
  {
    image: "boney_james.jpg",
    ticket:
      "https://www.tixr.com/groups/ampballantyne/events/boney-james-royal-summer-jazz-series-139371",
  },
  {
    image: "najee__regina_belle.jpg",
  },
  {
    image: "will_downing.jpg",
  },
];
//  \assets\img\najee__regina_belle.jpg
//  /assets/img/najee__regina_belle.jpg
</script>

<template>
  <div class="bg-black/50">
    <section class="max-w-screen-xl mx-auto bg-black/80 px-4 sm:px-10">
      <div class="grid items-center justify-center p-10">
        <LandingLogo class="h-[600px] fill-white" />
      </div>
      <div class="md:flex items-center gap-4 py-10">
        <template v-for="{ image } in events">
          <a class="block" href="https://www.ampballantyne.com">
            <img
              :src="`/_nuxt/assets/img/${image}`"
              alt="Image"
              height="auto"
              width="675px"
            />
          </a>
        </template>
      </div>
      <div class="p-10 text-center">
        <a
          class="inline-block border-white/50 border-2 bg-[#b46a20] text-[#f1ed74]/90 py-4 px-8 uppercase font-medium rounded-full "
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
          ><a href="https://embed-googlemap.com"
            >embed google maps in website</a
          >
        </div>
      </div>
    </section>
  </div>
</template>

<style>
html {
  background-color: black;
  background-image: url("/_nuxt/assets/img/black concrete.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-blend-mode: multiply;
  background-color: aliceblue;
}
.wrapper {
}
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
