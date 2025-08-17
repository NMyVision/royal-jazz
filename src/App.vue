<script setup lang="ts">
import Logo from './components/RoyalLogo.vue'
import VimeoVideoPlayer from './components/VimeoVideoPlayer.vue'

const videos = [
  {
    videoId: '1100358726',
    hostId: 'bd030f237b',
    title: 'Boney James Live at Royal Summer Jazz Series 2024',
  },
  {
    videoId: '1100358814',
    hostId: '8f893823e1',
    title: 'Najee Live at Royal Summer Jazz Series 2024',
  },
  {
    videoId: '1100358515',
    hostId: 'f820459fec',
    title: 'Dave Koz Live at Royal Summer Jazz Series 2024',
  },
]
</script>

<template>
  <div class="bg-cover min-h-full bg-[url(/1.jpg)] p-4 sm:p-10 md:p-20">
    <div
      class="bg-black/40 container py-8 p-4 sm:p-10 rounded-lg backdrop-blur-md border border-black max-w-[120ch] mx-auto"
    >
      <Logo class="size-40 fill-white/80" />

      <main class="space-y-6 text-white/80 mt-10 leading-relaxed">
        <p>
          <span class="font-semibold text-white">
            What an unforgettable summer! As the 2025 Royal Summer Jazz Series takes its final bow,
            we celebrate a season filled with incredible music, vibrant energy, and magical moments
            that brought the community together in style.
          </span>
        </p>

        <p>
          From the powerful performances of Boney James and Najee to the soulful elegance of Regina
          Belle and the dynamic artistry showcased throughout the series—each night delivered
          world-class jazz and an atmosphere filled with joy, connection, and pure musical
          excellence.
        </p>

        <p>
          We also want to thank our audience for your flexibility with weather-related schedule
          changes. While Mother Nature kept us on our toes, our commitment to delivering the best
          possible experience never wavered—and your continued support made all the difference.
        </p>

        <p>
          To our valued sponsors and partners—

          <span class="font-semibold text-white">
            TruCore Labs, Aloft Ballantyne Hotel, New York Life, Beasley Media Group, and
            Lowe's</span
          >—we are beyond grateful for your investment in the arts and your role in helping us bring
          this vision to life. A special thank-you to the
          <span class="font-semibold text-white">incredible volunteers from Bank of America</span>,
          whose energy, professionalism, and generosity helped create a welcoming and seamless
          experience for our guests.
        </p>

        <p>
          We also extend our
          <span class="font-semibold text-white"
            >deepest appreciation to the Charlotte Area Fund</span
          >
          for their continued support of cultural engagement and community advancement.
        </p>

        <p>
          And to <span class="font-semibold text-white">Positively Charlotte</span>, thank you for
          capturing the heart of the series through your live coverage and behind-the-scenes
          storytelling—your presence helped share the magic with an even wider audience.
        </p>

        <p>
          To our world-class artists, tireless crews, and the thousands of attendees who brought the
          series to life—thank you for making the 2025 Royal Summer Jazz Series one we'll never
          forget.
        </p>

        <p>
          <span
            >The Royal Summer Jazz Series is more than a concert—it's a celebration of culture,
            connection, and community.</span
          >
        </p>

        <p>
          We're already preparing for an even more exciting 2026 season—with new talent, elevated
          experiences, and more unforgettable nights to come.
        </p>

        <p>
          <span class="font-semibold text-white"
            >Until then, Stay smooth. Stay soulful. Stay <i >Royal</i>.</span
          >
        </p>
      </main>

      <article class="mt-20">
        <h3 class="font-light text-4xl/20 text-white">Recap Videos</h3>

        <div class="grid grid-cols-2 gap-8 mb-10">
          <template v-for="v in videos" :key="v.videoId">
            <VimeoVideoPlayer :videoId="v.videoId" :title="v.title" :hostId="v.hostId" />
          </template>
        </div>
      </article>
    </div>
  </div>
</template>
